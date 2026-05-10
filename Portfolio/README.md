# Randel Oropel — Portfolio Setup Guide

## Folder Structure

```
portfolio/
├── index.html              ← The portfolio itself
└── courses/
    ├── integrated-design-blueprint/   ← Your Rise 360 export folder
    │   ├── index.html
    │   ├── lib/
    │   ├── assets/
    │   └── ...
    └── your-next-course/              ← Future courses go here
        ├── index.html
        └── ...
```

## Setting Up Your First Course

1. Export your Rise 360 course as **Web** format.
2. Unzip the exported package.
3. Rename the unzipped folder to something URL-friendly (e.g. `integrated-design-blueprint`).
4. Place the entire folder inside `portfolio/courses/`.

The portfolio already references:
```
courses/integrated-design-blueprint/index.html
```
so if you name the folder `integrated-design-blueprint`, it will work automatically.

---

## Adding More Courses

Open `portfolio/index.html` in a text editor and find the **COURSE REGISTRY** section near the bottom:

```js
const COURSES = [
  {
    title:       "Integrated Design Blueprint",
    tag:         "Rise 360 · Web Export",
    description: "...",
    path:        "courses/integrated-design-blueprint/index.html",
    color:       "linear-gradient(135deg, #0b7a75 0%, #05504d 100%)"
  },
  // Paste a new object here for each additional course
];
```

**Fields:**
| Field | What to put |
|---|---|
| `title` | Display name of the course |
| `tag` | Short label (e.g. `Rise 360 · Web Export`) |
| `description` | One or two sentences shown on the card |
| `path` | Relative path to the course's `index.html` |
| `color` | CSS gradient for the card thumbnail |

**Palette colors for `color`:**
- Teal: `linear-gradient(135deg, #0b7a75 0%, #05504d 100%)`
- Copper: `linear-gradient(135deg, #bf4e30 0%, #7a2c18 100%)`
- Caramel: `linear-gradient(135deg, #f7b267 0%, #c4803a 100%)`
- Green: `linear-gradient(135deg, #c1edcc 0%, #6db880 100%)`

---

## Hosting

The portfolio is a static site — no server needed for most things. Options:

- **GitHub Pages** — free, upload the whole `portfolio/` folder
- **Netlify / Vercel** — drag & drop the folder, instant live URL
- **Local** — open `index.html` directly in a browser (note: iframes may be blocked locally; use a local server like VS Code Live Server instead)

> **Note on local iframes:** Browsers block `file://` iframes for security. Run a local server to preview courses inside the modal:
> ```
> npx serve portfolio
> ```
