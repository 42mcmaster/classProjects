# Team Spec Sheet — 01f: Networking Concepts

**Team members: ________________________________________**

Your sub-lesson: **Networking Concepts** (IC3 Objective 1.6) — the hardware, the vocabulary, and the famous troubleshooting order.
Your source of truth: **`dl1_01_StudyGuide.md`, Section 6.** Read it before you build anything.

Build slides 2–5 of your deck exactly as specified below (slide 1 = title, slide 6 = sources — see the Student Brief).

---

## Slide 2 — "The Boxes That Get You Online"

**Must-include facts (exact):**
- **Modem**: sends/receives between your home and the **ISP** over phone lines, fiber, or coax. **Router**: connects networks and forwards packets. **Network Adapter**: circuit board that connects a computer to a network.
- Connection technologies: **Ethernet** = wired LAN cables; **DSL** = telephone wires; **Cable** = TV coaxial cable.
- **Wired beats Wi-Fi on security and speed.** A phone connects via **Wi-Fi or a cellular data plan**.

**Go deeper (research required, cite your source):**
- A short history of the Internet: what was ARPANET, what year did it first connect computers, and when did the Internet open up to the general public? One sentence on how big it was then vs. now.

**PowerPoint requirement:** an inserted **picture** (modem/router photo — your own home setup counts — or a simple network diagram) — resized without distortion, **alt text** added, source cited on slide 6.

## Slide 3 — "Internet Vocabulary"

**Must-include facts (exact — all six):**
- **ISP**: company that connects you to the Internet. **DNS**: directory that maps names to Internet resources. **Default Gateway**: the device (usually your router) traffic passes through to reach the Internet. **HTML**: language used to build web pages. **Cookie**: text file tracking your activity on a site. **Breadcrumb**: trail to retrace your steps on a site.

**Go deeper:**
- Actually run `ipconfig` (Windows) on a lab machine: find the real default gateway address and DNS server. Put them on the slide.

**PowerPoint requirement:** a **table** (Insert > Table): Term | What it means — all six terms.

## Slide 4 — "No Internet? Fix It in Order"

**Must-include facts (exact — the order is the answer):**
1. **Check the hardware** (cables, power) → 2. **`ipconfig`** (IP starting with **169** = no valid IP) → 3. **`ping` / `tracert`** (gateway first, then `ping 8.8.8.8`) → 4. **DNS check** → 5. **Contact your ISP** → 6. **Check virus/malware protection**.
- Not sure you're online at all? **Open a browser and load a site.**

**Go deeper:**
- What is `8.8.8.8` actually? Who runs it and why does everyone ping it?

**PowerPoint requirement:** bulleted list with **two indent levels** — the six steps as main bullets, the key detail of each indented under it. (A numbered list is fine — it still needs the two levels.)

## Slide 5 — "The Lab Is Down (Quiz the Class)"

**Quiz the class:** give the class a scenario — "You get to the lab early and can't get online. What do you do FIRST?" — and offer three tempting choices (calling the ISP is the classic wrong first move). Take answers, then click to reveal.

**PowerPoint requirement:** the answer + one-sentence explanation gets an **entrance animation** so it stays hidden until you click.

---

**Fact check before you present:** every bolded term above appears on your slides, spelled and defined the way the Study Guide has it.
