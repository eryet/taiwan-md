# Design — Header & Homepage Exploration (WIP)

Design mockups and color reference for the Taiwan.md header redesign.

## Files

| File                           | Description                                                                                                                 |
| ------------------------------ | --------------------------------------------------------------------------------------------------------------------------- |
| `header-creative.html`         | **Proposed header** — open in browser. Responsive, live ZH/EN language switch. Includes hero + content section for context. |
| `header-mock.html`             | Reference mock of the current header with medium-width tightening fix (breakpoint at 1200px).                               |
| `homepage-redesign.excalidraw` | Early homepage layout wireframe (open in [excalidraw.com](https://excalidraw.com)).                                         |
| `taiwan-chic-jade-palette.svg` | Color palette reference — Taiwan Chic: Emerald (Jade), Pantone 3295 C.                                                      |

## Color Palette — Taiwan Chic: Emerald (Jade)

Based on [Ministry of Culture — Three Iconic Colors of Taiwan](https://www.moc.gov.tw/en/cp.aspx?n=3179).

| Variable          | Hex       | RGB             | Usage                                                    |
| ----------------- | --------- | --------------- | -------------------------------------------------------- |
| `--green-deep`    | `#004d40` | (0, 77, 64)     | Darkest — dropdown text, deep backgrounds                |
| `--green-primary` | `#006352` | (0, 99, 82)     | Primary dark                                             |
| `--green-mid`     | `#007864` | (0, 120, 100)   | **Pantone 3295 C** — active states, buttons, lang toggle |
| `--green-light`   | `#00997d` | (0, 153, 125)   | Hover states                                             |
| `--green-accent`  | `#4fd1b0` | (79, 209, 176)  | Bright accent — highlights, hero ".md" dot               |
| `--jade-soft`     | `#e0f2ef` | (224, 242, 239) | Light tint for backgrounds                               |

Source PDF: [Taiwan Chic Color Specification (文化部)](https://file.moc.gov.tw/001/Upload/OldFiles/AdminUploads/files/202212/9d3242be-2c9e-4530-896d-cc6880344d06.pdf)

## Header Changes Summary

### Desktop

- **Shorter EN labels** — "Knowledge Graph" → "Explore", "Geographic Taiwan" → "Map", etc.
- **No emojis in top-level nav** — kept in dropdown menus
- **GitHub as icon only** — no text label
- **Search button with `⌘K` badge** — collapses at medium widths
- **Nav separators** — subtle vertical lines grouping related items
- **Animated hover underlines** — grow from center
- **Smooth dropdown slide-in** — fade + translate animation
- **Fixed 56px height** — prevents CLS
- **Medium breakpoint (1200px)** — tightens padding/font instead of switching to hamburger
- **Serif logo font** — Noto Serif TC for "Taiwan.md"

### Mobile (768px)

- Same flat list structure as current site (kept as-is)
- Fixed 52px header height
- Search collapses to icon only

### Color

- Replaced generic leafy green palette with **Taiwan Chic Jade (Pantone 3295 C)**
- Green accent for active lang toggle instead of blue — matches brand identity
