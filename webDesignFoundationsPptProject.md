# Web Design Foundations PowerPoint Project

You will create a **7-slide PowerPoint deck** teaching one foundational web design topic from our list of **15 sections**.  

This project has two purposes:

1. **Continue Practicing Microsoft PowerPoint** skills needed for **Microsoft Office Specialist (MOS) certification** (themes, slide masters, SmartArt, charts, Alt Text, consistent layouts, speaker notes, accessibility).
2. **Teach your assigned web concept** clearly and visually to your peers.

---

## Deliverables

* **PowerPoint (.pptx)** named `LastName_WebDesignTopic.pptx`
* **Exported PDF** named `LastName_WebDesignTopic.pdf`
* Save in your GitHub repo folder named `webDesignPPT`
* Use the assigned section from the class list (1–15)

---

## Required Slide Outline

**Suggestion**: For the Visual Examples / Code Snippets, consider using the MARP versions of code snippets from VS Code. 

| Slide # | Content | Guidance |
|:--:|--|--|
| 1 | **Title Slide** | Topic Title, Student Name, Class/Year |
| 2 | **Definition / Purpose** | Clear 1–2 sentence definition of your concept (e.g., What is HTML? What does CSS do?) |
| 3 | **Key Terms & Elements** | List and explain 3–5 core tags, attributes, or terms relevant to your topic |
| 4 | **Visual Example / Code Snippet** | Include a screenshot or formatted code example (insert as image and ensure a meaningful **Alt Text** is added) |
| 5 | **Applied Example** | Show how your concept appears in an actual webpage screenshot or diagram |
| 6 | **Common Mistakes / Tips** | Explain 2–3 common errors students make and how to avoid them |
| 7 | **Key Takeaways** | Summarize why this topic is important and how it connects to later topics |

> *You may include one optional extra slide for “Bonus Info” or “Mini Quiz” if helpful.*

---

## PowerPoint Skills Checklist (MOS Prep)

| Skill | Description / Example |
|:--|:--|
| **Themes & Slide Master** | Apply one consistent theme. Edit fonts/colors in *View → Slide Master*. |
| **Layout Consistency** | Use the same text boxes, heading levels, and alignment across slides. |
| **SmartArt / Shapes** | Use SmartArt to visualize a process or hierarchy (Insert → SmartArt). |
| **Icons & Images** | Use meaningful visuals. Add **Alt Text** to each (Right-click → Edit Alt Text). |
| **Charts (optional)** | If relevant (e.g., form usage trends, HTML5 adoption), create a simple Excel chart and paste as **Linked Object**. |
| **Transitions & Animations** | Use subtle transitions; use animations at least once, but don't overuse it. |
| **Speaker Notes** | Add 1–2 sentences of talking points to at least 3 slides. |
| **Accessibility Review** | Use *Check Accessibility* under *Review* tab to verify readability. |

---

## Design & Accessibility Standards

* Minimum **24pt font** on slides.
* Maintain **contrast and whitespace** — avoid clutter.
* Use **one color palette** and **maximum of two font families**.
* **No text walls** — aim for 4–6 bullets per slide max.
* Add **Alt Text** for every image, icon, or code snippet image.
* Keep transitions simple and professional.

---

## Sources / Academic Honesty

* Include a final slide titled **References**.  
  List any sites, tutorials, or examples used (e.g., W3Schools, MDN, etc.).
* Write content in **your own words**.
* Do not copy-paste definitions directly from sources.

---

## Quick Student Checklist

* [ ] 7 slides completed following outline  
* [ ] Consistent theme + Slide Master used  
* [ ] Alt Text on all visuals  
* [ ] Use Icons in at least two places  
* [ ] Use Transition Effects for slides
* [ ] Use Animations on at least one slide    
* [ ] Speaker notes on ≥ 3 slides  
* [ ] Fonts ≥ 24pt and readable contrast  
* [ ] Saved as PPTX + exported as PDF  
* [ ] Uploaded to GitHub repo in folder `webDesignPPT`  
* [ ] References slide included  

---

## Shortcuts to Remember

* New Slide — **Ctrl + M**  
* Duplicate Slide — **Ctrl + D**  
* Save — **Ctrl + S**  
* Start Slideshow — **F5** | From Current Slide — **Shift + F5**  
* Group / Ungroup — **Ctrl + G / Ctrl + Shift + G**  
* Align Objects — *Format → Align → Left/Center/Right or Middle/Top/Bottom*  
* Paste Link Chart — *Home → Paste ▼ → Paste Special → Paste Link → Microsoft Excel Chart Object*

---

### Tip for Presenting:
Your deck and presentation should feel like a **mini-teaching tool** for the rest of the students.  
Make it visually clear, easy to follow, and professional — like you’re explaining this concept to someone new to web design.

---

## Student Assignments: 

**Note**: Don't worry about the competencies, that is for me (Mr. McMaster) and is based on your curriculum content.
**Note on HTML Forms Section**: This YouTube video maybe helpful for the individual doing part 5 HTML Forms: https://www.youtube.com/watch?v=fNcJuPIZ2WE


| Student # | Topic | Source Lesson (.md file) | Content Breakout (Content for Slides 2–7) |
| :---: | :--- | :--- | :--- |
| **1** | **HTML Basic Document Structure** | `html01.md` | **Definition:** HTML is a markup language describing the content and structure of web documents. **Key Terms:** `<!DOCTYPE html>`, `<html>`, `<head>`, `<body>`, Attribute. **Code/Visual:** Full basic HTML document structure example. **Applied:** Explain how `<title>` appears in the browser tab and search results. **Mistakes/Tips:** Forgetting required elements like `<!DOCTYPE html>` or `<head>`. Tip: Use comments to document code. **Takeaways:** HTML is the foundation (skeleton) of every webpage. |
| **2** | **HTML5 Semantic Sectioning** | `html02.md` | **Definition:** Semantic elements describe the meaning/structure of content for accessibility and search engine optimization (SEO), not just appearance.  Unlike non-semantic tags like `<div>` and `<span>`, which are generic, semantic tags such as `<header>`, `<nav>`, and `<article>` clearly define the purpose of the content they contain. This helps search engines understand the content and allows assistive technologies like screen readers to navigate the page more effectively.   **Key Terms:** `<header>`, `<nav>`, `<section>`, `<article>`, `<footer>`. **Code/Visual:** Example showing nested use of `<header>`/`<nav>` within an overall page structure. **Applied:** Explain when to use `<article>` (self-contained content like a blog post) vs. `<section>` (thematic grouping). **Mistakes/Tips:** Using `<div>` when a semantic element is available. Tip: Use only **ONE** `<h1>` and **ONE** `<main>` per page. **Takeaways:** Semantic structure improves accessibility and maintainability. |
| **3** | **Hyperlinks, Images, and Relative Paths** | `html03.md` | **Definition:** Hypertext links connect web pages using the `<a>` element, while the `<img>` element embeds content. **Key Terms:** `<a>`, `href`, `src`, `alt`, Relative URL, Absolute URL. **Code/Visual:** Example of an image link combined with an anchor link: `<a href="page.html"><img src="image.jpg" alt="Description"></a>`. **Applied:** Demonstrate the difference between relative path (`../images/img.jpg`) and absolute path (`http://example.com/img.jpg`). **Mistakes/Tips:** Forgetting the **required** `alt` attribute on images. Tip: Use descriptive link text (not "click here"). **Takeaways:** Links and images are crucial for navigation and content delivery (Core Competency 6.2). |
| **4** | **HTML Tables (Data Structure)** | `html04.md` | **Definition:** Tables organize tabular data into rows and columns, and should **not** be used for page layout. **Key Terms:** `<table>`, `<tr>`, `<td>`, `<th>`, `<caption>`, `colspan`. **Code/Visual:** Basic table structure using `<thead>`, `<tbody>`, and `<tfoot>`. **Applied:** Example using `colspan` to span a header across multiple columns. **Mistakes/Tips:** Using tables for page layout (use CSS Grid/Flexbox). Tip: Always use `<th>` for headers. **Takeaways:** Tables provide essential structure for data, aligning with data organization competency (6.1.6). |
| **5** | **HTML Forms: Structure and Methods** | `html05.md` | **Definition:** Forms collect user input and send it to a server for processing using `action` and `method` attributes. **Key Terms:** `<form>`, `action`, `method`, `name`, `label`, `required`. **Code/Visual:** Example demonstrating various input types (`text`, `email`, `number`) within a `<form>`. **Applied:** Explain the difference between **GET** (data visible in URL, for searches) and **POST** . **Takeaways:** Forms enable user interaction and are vital for data collection (Core Competency 6.4). |
| **6** | **CSS Basics & Types of Style Sheets** | `css01.md` | **Definition:** CSS describes how HTML elements should be visually displayed, separating content from presentation. **Key Terms:** Selector, Property, Value, Declaration. **Code/Visual:** Example of the CSS rule syntax (`Selector {property: value;}`). **Applied:** Compare the use cases of **External** (best practice, cacheable) vs. **Inline** (avoid for production, hard to maintain) styles. **Mistakes/Tips:** Forgetting the semicolon (;) to separate declarations. Tip: External style sheets are the preferred method for most websites. **Takeaways:** CSS is essential for modern design and maintainability. |
| **7** | **CSS Basic Selectors (Class, ID, Element)** | `css01.md` | **Definition:** Selectors target specific HTML elements to apply styles. **Key Terms:** Element Selector, Class Selector, ID Selector, Grouping Selector. **Code/Visual:** Code snippet showing `.class-name`, `#id-name`, and element selectors like `h1 {font-family: Arial;}` `p { }` selectors or grouping selectors which include more than one element like `h1, h2, p {font-family: Arial;}`. **Applied:** Explain when to use classes (reusable styles) vs. IDs (unique identifiers, used for JavaScript targeting). **Mistakes/Tips:** Forgetting the `#` for ID selectors or `.` for class selectors. Tip: Use descriptive class names (e.g., `.error-message`). **Takeaways:** Mastering selectors is the foundation for effective styling and specificity. |
| **8** | **CSS Colors and Accessibility** | `css02.md` | **Definition:** CSS color properties allow specification of color using different formats. **Key Terms:** RGB, Hexadecimal, HSL, RGBA/HSLA, Color Contrast. **Code/Visual:** Code showing one color defined in three ways: `color: rgb(255, 0, 0);`, `color: #FF0000;`, `color: hsl(0, 100%, 50%);`. **Applied:** Explain the role of the alpha channel in RGBA/HSLA for setting transparency (0 to 1). **Mistakes/Tips:** Using colors with poor contrast. **Takeaways:** Color choice impacts readability. |
| **9** | **The CSS Box Model** | `css03.md` | **Definition:** The box model describes the rectangular space an HTML element occupies, consisting of content, padding, border, and margin. **Key Terms:** Content, Padding, Border, Margin, `box-sizing: border-box`. **Code/Visual:** Diagram showing how margin, border, padding, and content add up to the total width/height. **Applied:** Code snippet demonstrating `box-sizing: border-box` (modern best practice) which makes sizing more intuitive. **Mistakes/Tips:** Confusion between padding (internal space) and margin (external space). Tip: Centering a block element horizontally using `margin: 0 auto;`. **Takeaways:** The box model is the fundamental principle for all layout and spacing in CSS. |
| **10** | **Advanced CSS Selectors & Pseudo-Classes** | `css04.md` | **Definition:** Advanced selectors target elements based on their position (contextual) or state (pseudo-classes). **Key Terms:** Descendant Selector (space), Child Selector (>), Pseudo-class (:hover), Pseudo-element (::before), Attribute Selector. **Code/Visual:** Code showing a pseudo-class example: `a:hover { color: red; }`. **Applied:** Example of using `::before` and the `content` property to insert generated content or icons. **Mistakes/Tips:** Misspelling pseudo-elements (using single colon `:` instead of double `::`). Tip: Define link styles in the correct order (LoVe HAte: :link, :visited, :hover, :active). **Takeaways:** These tools allow for precise styling and dynamic interactivity (6.2.7). |

---

## Helping section 10 Advanced CSS Selectors and Pseudo-Classes out a little bit: 

| **Pseudo-class** | **What it targets** | **Example** | **Meaning** |
|:------------------|:--------------------|:-------------|:-------------|
| `:hover` | When the mouse pointer is over the element | `a:hover { color: red; }` | Change the link color when the user hovers. |
| `:visited` | Links the user has already clicked | `a:visited { color: purple; }` | Show visited links in purple. |
| `:focus` | An element (like an input box) that’s currently active | `input:focus { border-color: blue; }` | Highlight the field that the user is typing in. |
| `:active` | The moment an element is being clicked | `button:active { transform: scale(0.98); }` | Slightly shrink the button when clicked. |

---

## Continuing: 

| Student # | Topic | Source Lesson (.md file) | Content Breakout (Content for Slides 2–7) |
| :---: | :--- | :--- | :--- |
| **11** | **JavaScript Functions, Objects, and Output** | `js00Part2.md`, `js01.md` | **Definition:** JavaScript provides behavior and interactivity. A **function** is a reusable block of code that performs a task; a **method** is a function belonging to an **object**. **Key Terms:** Function, Object, Method, String, `alert()`, `console.log()`. **Code/Visual:** Code showing the three main output methods: `alert('Hi');`, `console.log('Test');`, `document.write('Text');`. **Applied:** Explanation of the dot notation (`object.method()`), e.g., `document.write()`. In JavaScript, **dot notation** (`object.property` or `object.method()`) means: **object** → the thing you’re referring to (like `document` or `Math`), **`.`** → tells JavaScript to “look inside this object for…”, **property or method()** → the value or action you want to access or run.  **Mistakes/Tips:** Forgetting parentheses `()` when calling a function. Tip: The browser **Console** (F12) is the most important tool for learning and debugging. **Takeaways:** JS allows web pages to respond to user actions and modify content (Core Competency 6.3.2). |
| **12** | **JavaScript Variables and Data Types** | `js02.md` | **Definition:** Variables are labeled containers that store information in a program. **Key Terms:** `let`, `const`, String, Number, Boolean, `camelCase`. **Code/Visual:** Code demonstrating assignment and output using both `let` (changeable) and `const` (constant). **Applied:** Use template literals (backticks) to easily insert variables into strings: `` `Hello, ${userName}` ``. **Mistakes/Tips:** Trying to reassign a `const` value (causes an error). Tip: Default to `const` for safety, only use `let` if you know the value will change. **Takeaways:** Variables are fundamental for storing and manipulating data in any application logic. |
| **13** | **JavaScript DOM Manipulation (Selection & Content)** | `js04.md` | **Definition:** The DOM (Document Object Model) is JS's representation of the HTML structure, allowing scripts to find and modify elements. **Key Terms:** DOM, `getElementById()`, `querySelector()`, `textContent`, `innerHTML`, `classList`. **Code/Visual:** Code demonstrating selection: `const title = document.querySelector('#main-title');` followed by content change: `title.textContent = 'New Title';`. **Applied:** Show how to use `.classList.add('new-style')` to change multiple styles efficiently using a CSS class instead of direct style manipulation. **Mistakes/Tips:** Forgetting to store the selected element in a variable. Tip: Use `textContent` for plain text changes (safer); use `innerHTML` only when adding new HTML tags. **Takeaways:** This skill enables dynamic content updates necessary for interactive web apps. |
