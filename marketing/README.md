# Pilot Marketing AI Design System — Version 1.1

**Pilot's marketing AI design system for humans & AI where the `pilot-design-system.md` file is the source of truth.**

This repository contains the complete design system for building Pilot.com marketing pages — including all brand tokens, typography rules, color palette, component patterns, and brand assets.

---

## Repository Structure

```
├── pilot-design-system.md              # Source of truth — full design system reference
├── pilot-design-system-visualizer.html # Interactive visual preview (open in browser)
├── pilot-design-system-md-viewer.html  # Markdown renderer (embedded in visualizer)
├── pilot-slides-guidelines.md          # Slide deck brand guidelines
├── icons.md                            # Icon system specification
├── vercel.json                         # Hosting config (rewrites / → visualizer)
│
├── fonts/                              # Brand typefaces (Euclid Circular B, Space Mono, La Belle Aurore)
├── icons/                              # Icon assets (key color + alt color variants)
├── images/                             # Marketing images
└── logos/                              # Logo assets (SVG, PNG — multiple color variants)
```

---

## Quick Start

### 1. Clone the repository

```bash
git clone git@github.com:Pilot-Design-Team/marketing-website-design-system.git
cd marketing-website-design-system
```

Fonts, icons, and logos are included — no install step needed.

### 2. Open the visual preview

```bash
open pilot-design-system-visualizer.html
```

Or serve locally for the full experience (including the embedded markdown viewer):

```bash
npx -y serve .
```

### 3. Use in a project

Reference fonts locally from the `fonts/` directory:

```css
@font-face {
  font-family: 'Euclid Circular B';
  src: url('./fonts/EuclidCircularB-Regular-WebS.woff2') format('woff2'),
       url('./fonts/EuclidCircularB-Regular-WebS.woff') format('woff');
  font-weight: 400;
}

@font-face {
  font-family: 'Euclid Circular B';
  src: url('./fonts/EuclidCircularB-Semibold-WebS.woff2') format('woff2'),
       url('./fonts/EuclidCircularB-Semibold-WebS.woff') format('woff');
  font-weight: 600;
}
```

Copy the CSS variable block from **pilot-design-system.md § CSS Variables** into your project's `:root`.

---

## For AI & Vibecoding Tools

**Use a single consolidated reference:** [**pilot-design-system.md**](./pilot-design-system.md)

- **pilot-design-system.md** is the one comprehensive document covering all CSS variables, named colors, fonts, spacing, gradients, shapes, shadows, buttons, cards, forms, navigation, photography guidelines, background patterns, and brand philosophy.
- Attach or open **pilot-design-system.md** when building or editing any Pilot marketing page so all design system context is in one place.
- For a live visual preview of all tokens and components, open **pilot-design-system-visualizer.html** directly in a browser — no build step required.
- Follow the vibecoding constraints in the design system: no new fonts, no invented colors, left-align always, purple-only shadows, pill CTAs only.

---

## Design System Highlights

| Token | Value |
|---|---|
| Source of truth | `pilot-design-system.md` |
| Primary brand color | `#5931DC` — PILOT purple |
| Darkest anchor | `#281350` — PROFIT purple |
| Body font | Euclid Circular B (weights 300–700) |
| Tech/label font | Space Mono |
| Human accent font | La Belle Aurore (≤4 words max) |
| CTA border-radius | `999px` — always full pill |
| Text alignment | Left-align always — never centered |
| Drop shadows | Purple family only · blur 50–100px · opacity 10–20% |
| Container max-width | `75.5rem` (1208px) · 40px h-padding |

---

## Vibecoding Rules

When building with AI tools, enforce these constraints:

1. **No new fonts** — Only Euclid Circular B, Space Mono, La Belle Aurore
2. **No invented colors** — Use only named palette colors and CSS variables from the design system
3. **Left-align always** — Never center body text or headings
4. **Pill CTAs only** — All buttons use `border-radius: 999px`
5. **Purple shadows only** — Drop shadows use purple family colors only, never black or grey
6. **La Belle Aurore limit** — Maximum 4 words, never used for body text
7. **PROFIT as background, not fill** — `#281350` is never used as a circle fill
8. **Circles must be mathematically perfect** — `aspect-ratio: 1; border-radius: 50%`

---

## Assets

All assets are committed directly to this repo. Cloning automatically brings them down — no install step required.

- **fonts/** — Brand typefaces: Euclid Circular B (Regular + Semibold, woff/woff2), Space Mono (Regular/Bold/Italic), La Belle Aurore
- **logos/** — Full logos and lettermarks in SVG + PNG, across black/purple/white color variants
- **icons/** — Icon system assets in key color and alternate color variants (see `icons.md` for the full specification)
- **images/** — Marketing design reference images

---

## Updating the Design System

When brand rules, tokens, or components change:

1. Update **pilot-design-system.md** — this is the source of truth
2. Refresh the visual previews in **pilot-design-system-visualizer.html** to match
3. Commit both files together so they stay in sync

---

## Notes

- **Website:** [Pilot.com](https://pilot.com) — built on Webflow + custom CSS
- **Font licensing:** Euclid Circular B is licensed via Pilot — do not redistribute outside of Pilot projects

---

© Pilot.com, Inc.
