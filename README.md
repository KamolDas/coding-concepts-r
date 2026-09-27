# Coding Concepts — R Edition

The R companion to the Python "Coding Concepts" book. Same nine-module structure, same W/H concept table + mnemonic + copyable code + five-step learning cycle — mapped onto the R / tidyverse stack.

| # | Module | R equivalent of |
|---|--------|------------------|
| 1 | R Data Types | Python Data Types |
| 2 | Vectors & Apply | NumPy |
| 3 | dplyr | Pandas |
| 4 | ggplot2 | Matplotlib & Seaborn |
| 5 | Statistical Tests | SciPy |
| 6 | readxl / openxlsx | openpyxl |
| 7 | Shiny | PySide6 GUI |
| 8 | tidymodels | scikit-learn |
| 9 | Advanced AI (torch for R) | Advanced AI (PyTorch) |

## Architecture

Identical to the Python edition — content lives in `data/*.json`, rendered by a shared `chapter.html` + `assets/app.js`:

```
index.html          — landing page shell
chapter.html         — shared chapter template (?ch=1 … ?ch=9)
assets/
  styles.css         — shared visual styling
  app.js             — renders chapters/index from JSON, syntax-highlights code,
                       handles the copy button and localStorage persistence
data/
  chapters.json      — one row per chapter: id, module, title, tagline, nav label
  chapter1.json …9    — full content per chapter
wrangler.toml        — Cloudflare Pages project config
package.json         — npm run start / npm run deploy
```

To edit a chapter: open `data/chapterN.json`, change the text. To add a chapter: copy an existing JSON file, give it a new `id`, add a row to `data/chapters.json`.

## Running it locally

Pages load content with `fetch()`, so `file://` won't work — run a local server:

```bash
python3 -m http.server 8000
# or: npm start
```

## Deploying

### GitHub Pages
Push to GitHub → Settings → Pages → deploy from `main` / root. Or use GitHub's web "upload an existing file" flow to drag in every file without git.

### Cloudflare Pages — Dashboard (connected to Git)
Workers & Pages → Create → Pages → Connect to Git → **Build command: (empty)**, **Output directory: /**.

### Cloudflare Pages — Direct upload (no Git needed)
Workers & Pages → Create → Pages → **Upload assets** → drag this folder in → deploy. Re-upload any time you edit a JSON file.

### Cloudflare Pages — CLI
```bash
npm install
npx wrangler login
npm run deploy
```

## Progress

Each chapter's checklist and notes save to `localStorage`, scoped per chapter (`coding-concepts-ch1` … `ch9`). Nothing leaves the browser.

## Author

Kamol Das · Microbiology, University of Chittagong
