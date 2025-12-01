# Celadon 🍵

**An intellectual portfolio theme exploring the equilibrium between academic rigor and creative design.**

[Insert Screenshot of Homepage Here]

**Hugo Celadon** is a clean, responsive, one-page portfolio theme designed for **Academics**, **Data Scientists**, and **Creative Technologists**. It balances a rigorous publication list with a soft, "Morandi" color palette and modern grid layouts.

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

## ⚙️ Configuration
Celadon is configuration-driven. You can toggle and reorder sections in `hugo.toml`:

```toml
[params.homepage]
  sections = ["hero", "news", "research", "builds", "writing", "misc"]

  [params.homepage.hero]
    enable = true
    layout = "hero"

  [params.homepage.research]
    enable = true
    layout = "cards"
    title = "Selected Publications"
```
Refer to the full configuration options in `exampleSite/hugo.toml`.

## 📚 Content Types
Celadon supports two distinct content patterns:

- Direct Cards (Research/Builds): Items are displayed as cards with action buttons (PDF, Code, Demo). These link directly to external URLs or files.

- Deep Categories (Writing/Misc): Items are displayed as a "Curator Grid." Clicking a category (e.g., "Study Notes") takes the user to a dedicated sub-page list.

## ⚖️ License
This project is licensed under the MIT License - see the [LICENSE](https://github.com/Yajie-Xu/hugo-celadon/blob/main/LICENSE.txt) file for details.

## 👩🏻‍💻 Author
[Yajie Xu](https://yajiexu.com) &#124; [GitHub](https://github.com/Yajie-Xu)