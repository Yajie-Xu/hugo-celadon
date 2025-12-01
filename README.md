# Celadon 🍵

**An intellectual portfolio theme exploring the equilibrium between academic rigor and creative design.**

![celadon screenshot](https://github.com/Yajie-Xu/hugo-celadon/blob/main/images/screenshot.png?raw=true)


**Celadon** is a lightweight, responsive, one-page portfolio theme for [Hugo](https://gohugo.io). It is designed for **Academics**, **Data Scientists**, and **Creative Technologists**. It balances a rigorous publication list with a soft, "Morandi" color palette and modern grid layouts.

## ✨ Features

* **🎨 Morandi Design System:** A calm, high-contrast palette featuring Muted Teal, Warm Clay, and Cinnabar accents.
* **📜 One-Page Architecture:** A smooth-scrolling homepage that acts as a gateway to deep content.
* **🌙 Auto Dark Mode:** A sophisticated "Deep Slate" theme for low-light reading.
* **🧮 Academic Ready:** Native support for **KaTeX** (Math) and **Hugo Chroma** (Code Highlighting) with a "Gemini-style" copy interface.
* **🧩 Modular Sections:** Easily reorder sections (About, News, Research, Builds, Writing) via `hugo.toml`.
* **📱 Fully Responsive:** Collapsible layouts that look great on mobile and tablets.

## 🚀 Installation

### 1. Initialize Hugo
Inside your empty project folder:
```bash
hugo new site my-portfolio
cd my-portfolio
git init
```

### 2. Add Celadon Theme
```bash
git submodule add [https://github.com/Yajie-Xu/hugo-celadon.git](https://github.com/Yajie-Xu/hugo-celadon.git) themes/celadon
``` 
### 3. Update Configuration
Copy the `hugo.toml` from the exampleSite folder to your root, or add this to your existing config:

```toml
theme = "celadon"
```

## 📘 User Guide: Customizing Your Site

Celadon is designed to separate your **Content** (Markdown) from your **Homepage Layout** (Data).

### 1. Project Structure
Here is a map of what you should edit and what you can ignore.

```text
my-portfolio/
├── hugo.toml                <-- ⚙️ CONFIG: Menu, Title, Section ordering
├── content/                 <-- 📝 CONTENT: Your deep pages (Blogs, Papers)
│   ├── study/               
│   │   ├── _index.md        <-- Required for the section cover info
│   │   └── math-note.md     <-- Actual content page
│   └── _index.md            <-- Do not delete (Homepage entry point)
├── data/                    <-- 🗂️ HOMEPAGE DATA: Content for the main page cards
│   ├── news.yaml            <-- Matches "news" section
│   ├── research.yaml        <-- Matches "research" section
│   └── profile.yaml         <-- Your bio info
├── static/                  <-- 🖼️ ASSETS: Images, PDFs
│   └── images/              
├── themes/                  <-- ⛔ THEME: Do not edit directly
│   └── celadon/
│       ├── images/          
│       │   ├── tn.png       <-- Ignore (Required for Hugo Gallery)
│       │   └── screenshot.png <-- Ignore (Required for Hugo Gallery)
│       └── ...
└── ...
```
### 2. Managing the Homepage

The homepage is built dynamically based on your configuration.

**Step 1: Define Sections** Open `hugo.toml`. Under `[params.homepage]`, the `sections` list determines what appears and in what order.

````toml
[params.homepage]
  sections = ["hero", "news", "research", "writing"]
````
**Step 2: Create Matching Data Files** For every item in that list (e.g., `"writing"`), Hugo looks for a matching YAML file in the `data/` folder (e.g., `data/writing.yaml`).

- *Note*: The naming is case-insensitive, but keeping them lowercase is recommended.

**Step 3: Choose the Layout** In `hugo.toml`, tell Celadon how to render that section:

```toml
[params.homepage.writing]
  enable = true
  title = "Selected Writing"
  layout = "grid"  # Options: "hero", "news", "cards", "grid"
```

### 3. Creating Deep Pages (Sub-pages)

To link a Homepage Card (e.g., "Study Notes") to a list of actual articles:

**3.1. Create the Folder Structure** Inside `content/`, create a folder that matches your topic. You must include an `_index.md` file for the list layout to work.

```text
content/
└── study/
    ├── _index.md       <-- The "List" page definition
    ├── note-01.md
    └── note-02.md
```

**3.2. Configure** `_index.md` This file defines the title and description users see when they click through.

```markdown
---
title: "Study Notes"
description: "My raw notes on math and code."
layout: "list"
---
(Welcome text here...)
```
**3.3. Add Articles** Inside the same folder, add your individual notes or articles as separate Markdown files.

```markdown
---
title: "Understanding Eigenvalues"
date: 2025-11-20
summary: "A deep dive into eigenvalues and their applications."
image: "/images/EigenArt.png"
tags: ["Math", "Linear Algebra"]
---
(Content of the article...)
``` 
**3.4. Link it from the Homepage** Open your data file (e.g., `data/writing.yaml`) and set the `link` property to the folder path.

```yaml
items:
  - title: "Study Notes"
    image: "/images/cover.jpg"
    link: "/study/"   <-- This points to content/study/_index.md
```

### 4. System Files (What to Ignore)
If you look inside themes/hugo-celadon/, you will see specific image files required for theme submission. You do not need to replace these unless you are forking the theme to release your own version.

- images/screenshot.png: Used by the Hugo Theme Gallery to preview the theme.

- images/tn.png: A thumbnail used by the Hugo Theme Gallery.

- layouts/: The logic engine. Don't touch unless you are a developer modifying the core code.

## ⚖️ License
This project is licensed under the MIT License - see the [LICENSE](https://github.com/Yajie-Xu/hugo-celadon/blob/main/LICENSE.txt) file for details.

## 👩🏻‍💻 Author
[Yajie Xu](https://yajiexu.com)