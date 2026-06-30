# Randel Oropel — Portfolio Setup Guide

## Folder Structure

```
portfolio/
├── index.html              ← The portfolio itself
├── certs/                  ← Certification images for the hero carousel
│   ├── rise360-cert.png
│   ├── storyline-cert.png
│   └── ...
└── courses/
    ├── integrated-design-blueprint/   ← Rise 360 export folder
    │   ├── index.html       ← Rise 360 entry point
    │   ├── lib/
    │   ├── assets/
    │   └── ...
    ├── storyline-sample-1/            ← Storyline 360 export folder
    │   ├── story.html       ← Storyline entry point (NOT index.html)
    │   ├── html5/
    │   ├── mobile/
    │   ├── story_content/
    │   └── ...
    └── your-next-course/              ← Future courses go here
        └── ...
```

---

## Setting Up a Rise 360 Course

1. Export your Rise 360 course as **Web** format.
2. Unzip the exported package.
3. Rename the unzipped folder to something URL-friendly (e.g. `integrated-design-blueprint`).
4. Place the entire folder inside `portfolio/courses/`.
5. Its entry point is `index.html`.

---

## Setting Up a Storyline 360 Course

Storyline exports are structured differently from Rise — the entry point is **`story.html`**, not `index.html`, and the export includes folders like `html5/`, `mobile/`, and `story_content/`.

1. Export your Storyline course as **Web** format.
2. Unzip the exported package — you should see `story.html` plus `html5/`, `mobile/`, `story_content/` folders (and a couple of small support files like `meta.xml`).
3. Rename the unzipped folder to something URL-friendly (e.g. `storyline-sample-1`).
4. Place the entire folder inside `portfolio/courses/`.
5. Its entry point is `story.html` — keep the whole folder intact since Storyline's `story_content` and `html5`/`mobile` folders are required for it to run.

---

## Adding More Courses

Open `portfolio/index.html` in a text editor and find the **COURSE REGISTRY** section near the bottom:

```js
const COURSES = [
  // ── Rise 360 ──────────────────────────────────────────────
  {
    type:        "rise360",
    title:       "Integrated Design Blueprint",
    tag:         "Rise 360 · Web Export",
    description: "...",
    path:        "courses/integrated-design-blueprint/index.html",
    color:       "#0b7a75"
  },
  // ← Paste new Rise 360 objects here

  // ── Storyline 360 ─────────────────────────────────────────
  {
    type:        "storyline",
    title:       "Storyline Sample 1",
    tag:         "Storyline 360 · Web Export",
    description: "...",
    path:        "courses/storyline-sample-1/story.html",
    color:       "linear-gradient(135deg, #c1edcc 0%, #6db880 100%)"
  },
  // ← Paste new Storyline objects here
];
```

**Fields:**
| Field | What to put |
|---|---|
| `type` | `"rise360"` or `"storyline"` — controls which subsection on the page the card appears in |
| `title` | Display name of the course |
| `tag` | Short label (e.g. `Rise 360 · Web Export` or `Storyline 360 · Web Export`) |
| `description` | One or two sentences shown on the card |
| `path` | Relative path to the course's entry file — `index.html` for Rise 360, `story.html` for Storyline 360 |
| `color` | Hex color or CSS gradient for the card thumbnail |

Cards are automatically sorted into their **Rise 360** or **Storyline 360** subsection on the Portfolio page based on `type`, and the module count badge next to each subheading updates automatically.

**Palette colors for `color`:**
- Teal: `linear-gradient(135deg, #0b7a75 0%, #05504d 100%)` or `#0b7a75`
- Copper: `linear-gradient(135deg, #bf4e30 0%, #7a2c18 100%)` or `#bf4e30`
- Caramel: `linear-gradient(135deg, #f7b267 0%, #c4803a 100%)` or `#f7b267`
- Green: `linear-gradient(135deg, #c1edcc 0%, #6db880 100%)` or `#c1edcc`

---

## Adding Certifications to the Hero Carousel

The hero section has a right-hand column that auto-rotates through your certifications every 2.5 seconds (with dot indicators and a counter you can also click through manually).

1. Save each certification image into `portfolio/certs/` (PNG or JPG, landscape or portrait both work — it scales to fit).
2. Open `portfolio/index.html` and find the **CERTIFICATION CAROUSEL** section near the bottom (just above the `COURSE REGISTRY`):

```js
const CERTIFICATIONS = [
  {
    name:   "Articulate Rise 360 Certified",
    issuer: "Articulate",
    image:  "certs/rise360-cert.png"
  },
  {
    name:   "Articulate Storyline 360 Certified",
    issuer: "Articulate",
    image:  "certs/storyline-cert.png"
  },
  // ← Paste a new object here for each additional certification
];
```

**Fields:**
| Field | What to put |
|---|---|
| `name` | Certificate title, shown below the image |
| `issuer` | Issuing organization, shown under the name |
| `image` | Relative path to the image inside `portfolio/certs/` |

If an image path is missing or broken, the slide shows a placeholder box automatically instead of breaking — so it's safe to add an entry before the image file exists, then drop the image in later.

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
