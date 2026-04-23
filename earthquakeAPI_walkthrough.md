# Earthquake API Walkthrough

## From a live USGS feed to a map in Tableau Public 

**What you'll learn, and do:**

1. A real JSON file pulled from the USGS live earthquake feed.
2. A Python script (run in IDLE) that turns that JSON into a clean CSV.
3. A map and magnitude chart built from your CSV in Tableau Public.

**Tools we'll use:**

- A web browser (Chrome, Edge, Firefox, or Safari — any works).
- **IDLE** — Python's built-in editor. Already installed on lab machines.
- A free **Tableau Public** account.
  
---

## Part 0 — Setup (about 5 minutes)

### 0.1 Confirm IDLE opens

- **Windows:** Start menu → type `IDLE` → open **IDLE (Python 3.x)**.

You should see a window titled **Python 3.x.x Shell** with a `>>>` prompt. That's the Python interpreter. We'll come back to it.

### 0.2 Create a Tableau Public account

1. Go to **https://public.tableau.com/**
2. Click **Sign Up** (top right).
3. Use your school email or personal email. Pick a password you'll remember.
4. We are going to use the web-based version of Tableau Public, so we will "PUBLISH" our work to save it.

### 0.3 Make a working folder

In your documents folder, create a folder called `earthquake_lesson`. We'll save two files there:

- `earthquakes.json` — raw data from the API
- `earthquakes.csv` — cleaned-up version we'll feed Tableau

---

## Part 1 — What is an API?

**API** stands for **Application Programming Interface**. For our purposes today, think of it as a **web address that returns data instead of a web page**.

When you visit `https://www.cnn.com/`, the server sends back HTML — a web page your browser draws.

When you visit an API URL, the server sends back raw data — usually in **JSON** format — that a program can read.

### Anatomy of an API URL

```
https://earthquake.usgs.gov/fdsnws/event/1/query?format=geojson&starttime=2025-01-01&minmagnitude=6.0
└──────┬─────┘ └──────────┬──────────┘ └────────┬────────┘ │ └──────────────┬───────────────┘
  Protocol         Host (the server)           Path        ?        Parameters (filters)
```

Everything after the `?` is **parameters**. Parameters tell the server what you want. `&` separates them.

### What is JSON?

JSON is a text format that looks a lot like a Python dictionary — curly braces, keys, values:

```json
{
  "earthquake": {
    "magnitude": 6.5,
    "place": "off the coast of Chile",
    "depth_km": 25
  }
}
```

Python can read JSON directly with one line of code. We'll see that soon.

---

## Part 2 — Build your USGS query URL

The USGS (United States Geological Survey) publishes a free, public earthquake API. No key, no sign-up.

**Base URL:**

```
https://earthquake.usgs.gov/fdsnws/event/1/query
```

**Parameters we'll use:**

| Parameter | What it does | Example |
|---|---|---|
| `format` | Response format. We want `geojson` (easiest to parse). | `format=geojson` |
| `starttime` | Earliest date, `YYYY-MM-DD`. | `starttime=2024-01-01` |
| `endtime` | Latest date, `YYYY-MM-DD`. | `endtime=2024-12-31` |
| `minmagnitude` | Lowest magnitude to include. | `minmagnitude=6.0` |
| `maxmagnitude` | Highest magnitude to include (optional). | `maxmagnitude=9.9` |
| `limit` | Max number of results. Max allowed is 20000. | `limit=1000` |
| `orderby` | How to sort. Useful values: `time`, `magnitude`. | `orderby=magnitude` |

### Our starting query

Let's grab every earthquake of magnitude 6.0 or higher for the year 2024, sorted by magnitude (biggest first).

Copy this URL into a new browser tab:

```
https://earthquake.usgs.gov/fdsnws/event/1/query?format=geojson&starttime=2024-01-01&endtime=2024-12-31&minmagnitude=6.0&orderby=magnitude
```

You should see a wall of JSON text. That's it — that's an API call. You just made one.

> **Tip:** If the JSON looks like one giant unbroken line, click the `pretty-print` button/box in your browser, and it will clean up the view.

### Try a few variations before moving on

Change one parameter at a time and re-load the URL:

- Change `minmagnitude=6.0` to `minmagnitude=7.0`. Far fewer results.
- Change the year to `2023-01-01` / `2023-12-31`.
- Add `&limit=5` to the end to cap it at 5 rows.

**This is the whole point:** the URL *is* the query. You're already doing data engineering.

---

## Part 3 — Understand what we're pulling 

Before we parse anything, let's read the data that we got from the API query. The USGS GeoJSON response looks like this (simplified):

```json
{
  "type": "FeatureCollection",
  "metadata": { "count": 142, "generated": 1730000000000 },
  "features": [
    {
      "type": "Feature",
      "id": "us7000m1zt",
      "properties": {
        "mag": 7.0,
        "place": "153 km SSE of Sand Point, Alaska",
        "time": 1720000000000,
        "tsunami": 1,
        "felt": 12,
        "type": "earthquake",
        "url": "https://earthquake.usgs.gov/earthquakes/eventpage/us7000m1zt"
      },
      "geometry": {
        "type": "Point",
        "coordinates": [-160.75, 54.43, 33.2]
      }
    }
  ]
}
```

Each earthquake is one **feature** inside the `features` list. We care about the `properties` and the `geometry.coordinates`.

### Data dictionary (the fields we'll keep)

| JSON path | We'll call it | Type | Notes |
|---|---|---|---|
| `features[i].id` | `id` | text | Unique USGS event ID. |
| `features[i].properties.mag` | `magnitude` | number | Richter-style magnitude. |
| `features[i].properties.place` | `place` | text | Human-readable location. |
| `features[i].properties.time` | `time_utc` | text | Milliseconds since 1970 — we'll convert to a date. |
| `features[i].properties.type` | `event_type` | text | Usually `earthquake`, sometimes `quarry blast`. |
| `features[i].properties.tsunami` | `tsunami_flag` | 0/1 | 1 if tsunami advisory issued. |
| `features[i].properties.felt` | `felt_reports` | number | How many people filed a "Did You Feel It" report. |
| `features[i].properties.url` | `usgs_url` | text | Link to the USGS event page. |
| `features[i].geometry.coordinates[0]` | `longitude` | number | Note: **longitude is first** in GeoJSON. |
| `features[i].geometry.coordinates[1]` | `latitude` | number | Latitude is second. |
| `features[i].geometry.coordinates[2]` | `depth_km` | number | Depth in kilometers. |

That table **is** our plan for the CSV. Each row in the CSV will have exactly these columns.

---

## Part 4 — Save the JSON to your computer

With the USGS response still open in your browser:

- **Windows / Linux:** Press `Ctrl + S`.
- **Mac:** Press `⌘ + S`.

In the save dialog:

1. Navigate to your `earthquake_lesson` folder.
2. Name the file exactly **`earthquakes.json`** (lowercase, no spaces).
3. Save.

Open the folder and confirm the file is there. It should be around 100 KB if you used the query provided earlier.

> **Troubleshooting:** If your browser saves the file as `.txt` or adds extra extensions, rename it to `earthquakes.json`. Make sure your OS isn't hiding file extensions.

---

## Part 5 — Parse JSON → CSV with Python in IDLE

Now we'll write a small Python script that reads `earthquakes.json` and writes `earthquakes.csv` using only Python's built-in modules — **no installs needed**.

### 5.1 Make a new Python file

1. Open **IDLE**.
2. From the menu: **File → New File**. A blank editor window opens.
3. **File → Save As**, save into `earthquake_lesson` as **`parse_quakes.py`**.

### 5.2 Paste in the script

Copy this whole block into the editor window:

```python
# parse_quakes.py
# Read USGS earthquake GeoJSON and write a clean CSV for Tableau.

import json
import csv
from datetime import datetime, timezone

INPUT_FILE = "earthquakes.json"
OUTPUT_FILE = "earthquakes.csv"

# 1. Open the JSON file and load it into a Python dictionary.
with open(INPUT_FILE, "r", encoding="utf-8") as f:
    data = json.load(f)

# 2. Each earthquake is one entry in data["features"].
features = data["features"]
print(f"Loaded {len(features)} earthquakes from {INPUT_FILE}")

# 3. Build a list of clean rows.
rows = []
for feature in features:
    props = feature.get("properties", {})
    coords = feature.get("geometry", {}).get("coordinates", [None, None, None])

    # USGS time is milliseconds since Jan 1 1970 (epoch). Convert to a date string.
    time_ms = props.get("time")
    if time_ms is not None:
        time_str = datetime.fromtimestamp(time_ms / 1000, tz=timezone.utc).strftime("%Y-%m-%d %H:%M:%S")
    else:
        time_str = ""

    rows.append({
        "id":             feature.get("id"),
        "magnitude":      props.get("mag"),
        "place":          props.get("place"),
        "time_utc":       time_str,
        "event_type":     props.get("type"),
        "tsunami_flag":   props.get("tsunami"),
        "felt_reports":   props.get("felt"),
        "usgs_url":       props.get("url"),
        "longitude":      coords[0],
        "latitude":       coords[1],
        "depth_km":       coords[2],
    })

# 4. Write the rows to CSV.
fieldnames = [
    "id", "magnitude", "place", "time_utc", "event_type",
    "tsunami_flag", "felt_reports", "usgs_url",
    "longitude", "latitude", "depth_km",
]
with open(OUTPUT_FILE, "w", newline="", encoding="utf-8") as f:
    writer = csv.DictWriter(f, fieldnames=fieldnames)
    writer.writeheader()
    writer.writerows(rows)

print(f"Wrote {len(rows)} rows to {OUTPUT_FILE}")
```

### 5.3 Run it

From the IDLE editor window: **Run → Run Module** (or press **F5**).

IDLE will flip over to the Python Shell and you should see something like:

```
Loaded 99 earthquakes from earthquakes.json
Wrote 99 rows to earthquakes.csv
```

Open the `earthquake_lesson` folder. You should now have `earthquakes.csv`. Double-click it — Excel, Numbers, or whatever opens CSVs on your machine will show you a real table.

### 5.4 What the code is doing (plain English)

1. `json.load(f)` — reads the whole JSON file into Python as a nested dictionary.
2. `data["features"]` — grabs the list of earthquakes.
3. The `for feature in features:` loop visits each earthquake one at a time.
4. `.get("mag")` is a safe way to pull a field: if it's missing, you get `None` instead of a crash.
5. The time conversion turns USGS's millisecond timestamp into a readable date.
6. `csv.DictWriter` writes each row using our column names.

### 5.5 Common things that go wrong

- **`FileNotFoundError: earthquakes.json`** — The script and the JSON must be in the same folder. In IDLE, make sure `parse_quakes.py` was saved *into* `earthquake_lesson`, not into Documents.
- **`KeyError: 'features'`** — The JSON you saved isn't what we expected. Open `earthquakes.json` in IDLE (File → Open) and check that it starts with `{"type":"FeatureCollection"`. If it doesn't, your URL probably returned an error — re-check the parameters.
- **Empty CSV / only headers** — Your query returned zero results. Lower `minmagnitude` or widen the date range.

---

## Part 6 — Build a map in Tableau Public

### 6.1 Open Tableau Public Desktop

Launch **Tableau Public Desktop**. You'll land on a start page with a **Connect** panel on the left.

### 6.2 Connect to the CSV

1. Under **Connect → To a File**, click **Text file**.
2. Browse to `earthquake_lesson/earthquakes.csv` and open it.
3. Tableau shows a preview of your data. Confirm the columns look right (`magnitude`, `place`, `latitude`, `longitude`, etc.).

### 6.3 Set geographic roles

Tableau usually auto-detects `latitude` and `longitude`, but let's make sure.

1. In the **Data** pane (left side), find `Latitude`. Right-click → **Geographic Role → Latitude**.
2. Same for `Longitude` → **Geographic Role → Longitude**.
3. Move `Latitude` and `Longitude` to `Dimensions` — we want them treated as locations, not numbers to calculate (which is what `Measures` are).

They should both have a little globe icon appears next to each — that's how you know Tableau will be able to map them.

### 6.4 Make the map

1. Click **Sheet 1** at the bottom to open a worksheet.
2. Drag **Longitude** to the **Columns** shelf at the top.
3. Drag **Latitude** to the **Rows** shelf.
4. To be safe and to ensure we differentiate all "dots" on the map, in the Data pane, find **Id** (the unique quake ID). Drag it onto **Detail** on the Marks card.  This will ensure we are seeing all individual quakes.  

### 6.5 Make it readable

- Drage **Magnitude** to `dimensions` which will make it a category rather than do a calculation on it like `sum` or `avg`. 
- Let's duplicate the **Magnitude** variable and then drag that duplicate back to the `measures` section.
- Drag the `dimensions` version of **Magnitude** onto **Size** on the Marks card. Bigger quakes → bigger dots.
- Drag the `measures` version of **Magnitude** onto **Color** on the Marks card. Stronger quakes → darker color.
- Drag **Place** onto **Tooltip** so hovering shows the location.

Congratulations — that's a published-quality map of real seismic data that didn't exist in a spreadsheet ten minutes ago.

### 6.6 Save to Tableau Public

**Publish As** — give the workbook a name, and it publishes to your public profile. Share the URL with anyone you'd like.

---

## What you learned

- An **API** is just a URL that returns data.
- **Parameters** on a URL are how you filter and shape what comes back.
- **JSON** is structured text; Python's `json` module turns it into a dictionary with one line.
- **GeoJSON** from USGS wraps each earthquake in a `feature` object with `properties` and `geometry`.
- Flattening nested JSON into a **CSV** is how you bridge from "API-world" to "Tableau-world."
- Tableau Public can go from CSV → map in under five minutes once the columns are named well.

---

## Quick reference — the full URL parameters cheat sheet

| Parameter | Example | Notes |
|---|---|---|
| `format` | `geojson` | Always use this for our workflow. |
| `starttime` | `2024-01-01` | Inclusive. |
| `endtime` | `2024-12-31` | Inclusive. Omit for "through now." |
| `minmagnitude` | `4.5` | Lowering this quickly explodes the row count. |
| `maxmagnitude` | `9.9` | Rarely needed. |
| `limit` | `1000` | Max 20000. Use with `orderby`. |
| `orderby` | `magnitude` | Or `time`, `time-asc`, `magnitude-asc`. |
| `minlatitude` / `maxlatitude` | `25` / `50` | Bounding box — filter to a region. |
| `minlongitude` / `maxlongitude` | `-125` / `-65` | Example above ≈ continental US. |

Full API docs: **https://earthquake.usgs.gov/fdsnws/event/1/**
