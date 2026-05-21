# Pilot Slides: LLM Creation Guidelines

> **Purpose:** Instructions for an LLM to generate Google Slides content that is on-brand,
> structurally consistent, and visually appropriate for Pilot.com presentations.
> Source: HAKUNA [2026-02-26] All Hands deck + Pilot Brand & Marketing Design System.

---

## 1. Overview & Philosophy

Pilot slides are **direct, confident, and information-dense without feeling cluttered**. The
deck does not over-explain. Typography does the heavy lifting — bold weight signals the
most important idea on the slide, and whitespace creates emphasis. Every slide should feel
like it belongs to a single, coherent visual system: purple + white + near-white, with
structure that always anchors text to the left.

**The LLM's job is to:**
1. Choose the right layout template for the content type.
2. Apply color and typography rules consistently.
3. Never make decorative choices that conflict with the brand system.

---

## 2. Brand Foundations

### 2.1 Color Palette

All slide backgrounds, text, and shapes pull from this palette only. Do not introduce
colors outside this system.

#### Purple Scale (Primary)
| Name     | Hex       | In-Slide Role |
|----------|-----------|---------------|
| Profit   | `#281350` | Darkest backgrounds, section dividers |
| Pilot    | `#5931DC` | Primary brand purple — use for hero/section title slides |
| Brilliant| `#825BEB` | Secondary purple elements |
| Highlight| `#DECEFF` | Subtle light purple accent |
| Margin   | `#F6F3FF` | Default light slide background (near-white with a purple tint) |

#### Secondary (Accent) Colors
Use **subdued variants** by default. Only use the `+` vibrant variants as a single
accent per slide, and never as a background fill on large areas.

| Name      | Hex       | Use Case |
|-----------|-----------|----------|
| Access    | `#FCF3D6` | Warm callout cards, "highlight" chips |
| Clarity   | `#FBEDFF` | Cool light backgrounds, secondary panels |
| Trust     | `#E7F9FF` | Blue-tinted callout areas |
| Access+   | `#FFD967` | Single accent only — sparingly |
| Clarity+  | `#F891FF` | Single accent only — sparingly |
| Trust+    | `#8EECFF` | Single accent only — sparingly |

#### Neutrals
| Name        | Hex       | Use |
|-------------|-----------|-----|
| Pilot Black | `#3F3C3D` | All body text on light backgrounds |
| White       | `#FFFFFF` | Text on dark/purple backgrounds; card fills |
| Light Gray  | `#E0E0E0` | Dividers, subtle borders |
| Off-White   | `#F8F8F8` | Card chip backgrounds |

---

### 2.2 Typography

Pilot uses **three typefaces**, each with a distinct role:

- **Euclid Circular B** (Poppins as slide fallback) — primary face for all headings and body copy
- **Space Mono** — tech/precision labels, eyebrows, metadata only
- **La Belle Aurore** — human accent, script/cursive, ≤4 words only. Introduces warmth and imperfection. Use when the content is closer to the "people" end of the People ↔ Tech spectrum. **Never use for more than 4 words. Never use as a crutch.**

#### Font Usage Rules

| Element | Font | Weight | Notes |
|---------|------|--------|-------|
| Hero / Section title (large) | Euclid Circular B / Poppins | **Bold (700)** | Very large — often 60–80pt |
| Slide title | Euclid Circular B / Poppins | **SemiBold (600)** | 28–40pt |
| Supporting subtitle (same slide as title) | Euclid Circular B / Poppins | Regular (300–400) | Lighter weight, same or slightly smaller size |
| Body copy | Euclid Circular B / Poppins | Regular (400) | 14–16pt |
| Bold emphasis within body | Euclid Circular B / Poppins | **Bold (700)** | Used inline for key phrases |
| Labels / Eyebrows / Metadata | Space Mono | Regular (400) | ALL CAPS, 10–12pt |
| Footer text (PROJECT, DATE) | Space Mono | Regular (400) | ALL CAPS, small (~10pt) |
| Human accent phrase | La Belle Aurore | Regular (400) | ≤4 words, ~24–28pt, color `#281350`. Warmth/people context only. |

#### Typography Behavior Rules
- **All text is left-aligned.** Text can also be right-aligned in exceptional circumstances. **Text must never be centered** — no exceptions in standard content slides. *(Layout 9 — Statement — is the one slide-specific exception where a single short provocation may appear vertically and horizontally centered, due to deliberate negative space as a design choice.)*
- On **dark (purple) panels**, text is always white.
- On **light panels**, titles use `#5931DC` (Pilot Purple) or `#281350` (Profit/dark purple).
  Body copy uses `#3F3C3D` (Pilot Black).
- **Mixed weight in a single headline** is a key design pattern:
  - Bold word(s) anchor the key idea; regular/light weight word(s) set the context.
  - Example: **"5 consecutive quarters"** (bold) + "of net sales growth" (regular)
  - On light backgrounds: bold part in `#5931DC`, rest in `#281350` or matching purple.
  - On dark (purple) backgrounds: both parts in white, with the bold visually popping.

---

### 2.3 Layout Grid & Margins

- Slides are **16:9 widescreen** (1920×1080px or equivalent aspect ratio).
- **Safe margin:** ~5–6% from all edges (roughly 60–80px at 1080p).
- **Left panel width** (when using split layouts): ~40% of slide width.
- **Right panel width:** ~60% of slide width.
- Content cards/panels use **rounded corners** (`border-radius: 16–24px`).
- The **header strip**: Year (`2026`) sits top-left; `PILOT.COM` or `CONFIDENTIAL` sits top-right. Both in Space Mono, small, muted purple.
- The **footer strip**: `PROJECT [name]` left, `DATE [Month Year]` center-left, Pilot `p` mark bottom-right. All in Space Mono, small, muted purple. A thin purple line (`#5931DC`) or lavender bar runs across the very bottom edge.

---

### 2.4 Background Patterns

Two primary background treatments appear in the deck:

1. **Gradient Purple** — Used for cover/title slides. Linear gradient `135deg` from
   `#281350` (dark) to `#5931DC` (Pilot purple). Sometimes a dot-matrix pattern
   (small white circles in a grid at the bottom, fading out) is layered over this.
   Per brand guidelines, gradients should stay within the same tonal family.
2. **Margin (near-white)** `#F6F3FF` — Used for most content slides as the base.
3. **Split Light/Dark** — Left half is `#F6F3FF` (near-white), right half is `#5931DC`
   (solid Pilot Purple). A hard vertical split, no gradient between them.
4. **Clarity (lavender)** `#FBEDFF` — Used as full-bleed background for "social proof"
   and screenshot slides.

---

## 3. Slide Layout Templates

Use the decision tree in Section 4 to choose which template to apply. Below are all
templates observed in the deck, with exact construction instructions.

---

### Layout 1: Cover / Event Title Slide

**Use for:** Opening slide, closing slide, major section openers when you want a bold brand moment.

**Construction:**
- Full-bleed background: **Gradient Purple** (`#5931DC` → `#281350`).
- Optionally: dot-matrix pixel pattern overlaid at bottom third (white dots, low opacity).
- Center of slide: Pilot wordmark logo in white.
- To the right of the logo: a thin vertical white rule (`1–2px`), then the event/deck
  name in white, **SemiBold**, large (36–48pt). Two lines, e.g.:
  ```
  All
  hands
  ```
- Top-right corner: `PILOT.COM` in Space Mono, white, ~10pt.
- No footer bar on this layout.

**When to use:** Opening or closing slide only. Also used as the visual "wallpaper" between
major agenda sections in this deck.

---

### Layout 2: Section Divider (Bold Color Block)

**Use for:** Announcing a new agenda section. High visual impact, minimal text.

**Construction:**
- Full-bleed background: **Solid Pilot Purple** (`#5931DC`).
- Single word or very short phrase, top-left area (not centered), massive type:
  - Font: Euclid Circular B / Poppins, **Bold**, ~80–96pt.
  - Color: **White**.
  - Example: `CEO`, `Trials`, `AGENDA`.
- Header strip: Year top-left, `PILOT.COM` top-right — both white.
- Footer strip: PROJECT, DATE labels in white (muted). Pilot `p` mark bottom-right, white.

**When to use:** Exactly when transitioning between major agenda sections. No body content.
One word or two words maximum.

---

### Layout 3: Section Title (Light Background, Oversized Type + Grid Texture)

**Use for:** Section-opening "framing" slides — typically the first content slide after a
Section Divider. Sets up the narrative of what's about to be covered.

**Construction:**
- Full-bleed background: **White** (`#FFFFFF`).
- Right ~30–40% of slide: a subtle grid/graph-paper pattern in lavender (`#DECEFF`
  or `#E3DAFD`), fading to white toward the center. Used as a textural element only.
- Left ~60% of slide: oversized title text, top-left aligned:
  - Line 1: Key word or year in **Bold**, very large (~72–80pt), color: `#5931DC`.
  - Line 2: Context phrase in **Light/Regular**, same large size (~72–80pt),
    color: `#5931DC` or `#281350`.
  - Example: **`2026`** (bold) + `in context` (light).
- Below the title: optional small subtitle — `SemiBold`, ~18–20pt, dark purple `#281350`.
- Header strip: Year top-left `#8258EB` muted, `PILOT.COM` top-right muted.
- Footer: PROJECT/DATE Space Mono labels in muted purple, thin purple bottom bar.

**When to use:** When introducing a new framing concept with a short phrase. Works best
with 2–4 words max. Do not add body copy to this layout.

---

### Layout 4: Two-Column Split (Light Left / Dark Right)

**Use for:** The primary "meat" layout — a framing headline on the left and supporting
detail (bullets, quotes, numbered items) on the right. The most common layout in the deck.

**Construction:**
- **Left panel** (~40% width): Background `#F6F5FF` (Margin/near-white).
  - Slide title/label at the top-left, in purple. Can be a two-line mixed-weight headline.
  - Optional: a small subtitle or supporting sentence below (regular weight, dark purple).
  - Nothing else in this panel — it should feel spacious.
- **Right panel** (~60% width): Background **Solid Pilot Purple** `#5931DC`.
  - Content in white text.
  - Use **numbered items** (circled numbers `①②③`) or **arrow bullets** (`→`) to list
    points. Numbers are in outline/circle style, ~24–28pt.
  - Item label: **Bold**, ~14–16pt, white.
  - Item description: Regular, ~12–14pt, white.
  - 2-column arrangement within the right panel works well for 3–4 items (items in a 2×2 grid).
  - Pilot `p` mark, bottom-right of right panel, muted.

**When to use:**
- Numbered or bullet reasoning (3–4 supporting points).
- "Here's why" or "Here's how" content.
- Any slide where a framing label pairs with detailed supporting points.

**Typography detail:** The left panel title often uses the mixed-weight pattern:
- Bold key phrase in `#5931DC`, regular modifier text in `#281350` or matching hue.

---

### Layout 5: Two-Column Split (Light Left / Light Purple Right)

**Use for:** Data + context slides where the right panel shows a chart, table, or
screenshot — content that needs a lighter backdrop than solid purple.

**Construction:**
- **Left panel** (~30–35% width): Background `#FFFFFF` or `#F6F5FF`.
  - Eyebrow label in Space Mono, ALL CAPS, small, muted purple — e.g. `WHERE DO THEY COME FROM?`
  - Main headline below in **Bold**, `#281350` or `#5931DC`. ~28–36pt.
- **Right panel** (~65–70% width): Background `#F8EDFF` (Clarity/lavender).
  - Chart, table, or data visualization centered in the panel.
  - Charts use purple shades (`#5931DC`, `#8258EB`, `#DECEFF`) — not green/red for
    positive/negative; use varying purple shades instead.
  - White rounded card (`border-radius: 16px`) wrapping the chart adds a clean layer.

**When to use:**
- Charts and graphs (bar, line, funnel).
- Data tables.
- Product screenshots (place inside the white card).

---

### Layout 6: Diagram / Framework Slide (Light Background, Full-Width)

**Use for:** Visual frameworks, architecture diagrams, process flows, relationship maps.

**Construction:**
- Full-bleed background: `#F6F5FF` (Margin) or `#FFFFFF`.
- Title: Top-left, **SemiBold**, ~24–28pt, `#281350`.
- Diagram fills the right ~70% of the slide.
- Diagram elements use:
  - **Solid purple cards** (`#5931DC`): Primary/active items.
  - **Cream/warm cards** (`#FCF3D6`): Secondary or inactive items.
  - **Light purple cards** (`#F8EDFF`): Supporting items.
  - **Curly brace or bracket** annotations above groups (in dark purple `#281350`).
  - Arrow connectors: thin, dark purple `#281350`.
  - Card corner radius: `12–16px`. Cards are squarish, not wide rectangles.
  - Item labels inside cards: **SemiBold**, white (on purple cards) or `#281350` (on light cards), ~12–14pt.
- Horizontal "row" items spanning full diagram width (e.g., "Free trials") use a
  lighter purple fill (`#F0ECFD` or `#E3DAFD`) with `#5931DC` text.

**When to use:**
- GTM or org structure diagrams.
- Product architecture.
- Process flow (multi-step with grouped lanes).

---

### Layout 7: Left Label + Right Data Card

**Use for:** "Here is the supporting evidence" — a framing label on the left, and a
single large data visualization or product screenshot in a white card on the right.

**Construction:**
- Full-bleed background: `#F8EDFF` (Clarity/lavender) or `#F6F5FF`.
- **Left side** (~35% width):
  - Optional eyebrow label in Space Mono, muted purple, small, ALL CAPS.
  - Main headline in **SemiBold**, ~24–32pt. Mix bold + regular weights for key vs. context.
  - Color: `#281350` or `#5931DC`.
- **Right side** (~65% width):
  - White rounded card (`border-radius: 16–24px`, white fill, subtle drop shadow optional).
  - Card contains: chart, table, screenshot, or diagram.
  - The card sits with ~24px margin from the right/top/bottom edges of the slide.

**When to use:**
- Bar charts with a contextual label.
- Product UI screenshots.
- Workflow screenshots.
- Any single data asset that benefits from card framing.

---

### Layout 8: Full-Bleed Screenshot / Social Proof

**Use for:** Showing a real-world artifact — a Slack message, email, browser window, or
product screenshot — as the primary content. Minimizes slide chrome.

**Construction:**
- Full-bleed background: `#F0ECFD` (light lavender) or `#F6F5FF`.
- The artifact (Slack message, email, etc.) is placed in a **white rounded card**
  (`border-radius: 16–20px`), centered on the slide with generous padding on all sides.
  Card fills roughly 70–80% of the slide area.
- No title text on the slide. The artifact content speaks for itself.
- Footer strip as usual (Space Mono metadata, thin purple bar).

**When to use:**
- Customer messages, Slack snippets, social posts.
- Product "Payment Successful" or UI flow confirmations.
- Real evidence / social proof moments.
- AI agent output examples.

---

### Layout 9: Statement / Provocation (Light Background, Single Centered Sentence)

**Use for:** A single bold statement meant to land as a punchline or provocation. Minimal
design, maximum white space.

**Construction:**
- Full-bleed background: `#F6F5FF` or `#FFFFFF`.
- A single sentence or phrase, **vertically and horizontally centered** on the slide
  (this is the **only layout where centering is appropriate**).
  - Font: Euclid Circular B / Poppins, Regular or Light, ~36–48pt.
  - Color: `#281350` (dark purple) or `#5931DC`.
  - The sentence is intentionally incomplete or provocative — e.g.: `____ kills all deals.`
- Nothing else on the slide except the standard footer.

**When to use:**
- Rhetorical questions or provocations.
- Transition beats where you want the room to pause.
- A single big reveal statement before the follow-up slide.

---

### Layout 10: Quote Slide (Split, Dark Right Panel)

**Use for:** External quotes, customer testimonials, or a key attributed insight.

**Construction:**
- Same split as **Layout 4** (light left, dark purple right).
- **Left panel**: Short topic label or question — e.g. `What are agents?`. Mixed-weight
  headline, **Bold** + Regular, `#5931DC`.
- **Right panel** (solid `#5931DC`):
  - Opening quotation mark `"` (implied via inline text), then the quote in white,
    Regular or Light, large type (~32–40pt).
  - Attribution below: Space Mono, ALL CAPS, small, white or `#DECEFF`.
  - Example: `SIMON WILLISON`
- No bullet points. Quote stands alone.

**When to use:**
- External expert quotes.
- Defining a concept through someone else's words.
- Customer testimonials (use a shorter version of the social proof card instead if
  the quote comes with a screenshot).

---

### Layout 11: Agenda Slide

**Use for:** The deck agenda / table of contents. Appears near the beginning.

**Construction:**
- Full-bleed background: `#F6F5FF` or `#F8F8F8`.
- Top-left: `AGENDA` label in **Bold**, ~28–36pt, `#5931DC`. All caps or title case.
- Right ~60% of slide: Agenda items as a vertical list.
  - Each item: Regular weight, ~18–22pt, `#5931DC` or `#281350`.
  - Items are listed with light spacing between them — no bullet points, no numbers.
  - Active/highlighted section: can be **SemiBold** or slightly larger.
- Bottom-right: Small Pilot `p` mark, muted.
- Footer strip as usual.

**When to use:** Only once at the start of the deck.

---

### Layout 12: Template / Lorem Ipsum Reference Slide

**Use for:** This layout appears in the deck as a master reference showing the two variants
side by side. **Do not use this layout for real content** — it exists only to demonstrate
the two-panel system.

**Construction:**
- Left half: light panel with title + two-column body copy (two paragraphs).
- Right half: dark purple panel with same title + bulleted list using `→` arrows.
- Demonstrates the paired nature of light/dark layout variants.

---

## 4. Layout Decision Tree

When given content to put on a slide, follow this logic:

```
Is this an opening/closing or major section break?
  → YES: Is it the very first/last slide?
      → YES: Use Layout 1 (Cover)
      → NO: Use Layout 2 (Section Divider)

Is this a framing/intro slide for a new topic with just a headline phrase?
  → YES: Use Layout 3 (Section Title — light, oversized type)

Does the slide have a key idea on the left + supporting detail on the right?
  → YES: Is the right side a list/bullets/numbered points?
      → YES: Use Layout 4 (Split Light/Dark)
  → YES: Is the right side a chart, table, or data?
      → YES: Use Layout 5 (Split Light/Light Purple) or Layout 7 (Left Label + Card)

Is the slide a framework, architecture, or process diagram?
  → YES: Use Layout 6 (Framework/Diagram)

Is the slide showing a real-world artifact (Slack, email, product screenshot)?
  → YES: Use Layout 8 (Full-Bleed Screenshot)

Is the slide a single bold statement or rhetorical provocation?
  → YES: Use Layout 9 (Statement)

Is the slide an external quote or attribution?
  → YES: Use Layout 10 (Quote)

Is this the agenda?
  → YES: Use Layout 11 (Agenda)
```

---

## 5. Typography Emphasis Rules

### The Mixed-Weight Headline Pattern

The most distinctively Pilot typographic pattern. Always apply when a title has two
semantic parts: a **key noun/metric** and a **context modifier**.

```
Bold part   → the thing that matters / the number / the product name
Light part  → the qualifier, the "so what", the category
```

**Examples from the deck:**
- `5 consecutive quarters` (bold, purple) + `of net sales growth` (light/regular, dark purple)
- `2026` (bold, purple) + `in context` (light, purple)
- `Easy` (bold) + `money.` (regular)
- `2025 was a` + `record-breaking year.` (bold)
- `What` + `we're building` (bold)

**Color rule on mixed headlines:**
- On light background: bold word = `#5931DC`, regular word = `#281350` or same purple.
- On dark (purple) background: both = white, bold carries visual weight via weight alone.

---

### Space Mono Usage

Space Mono appears **only** in:
1. Eyebrow/category labels above a headline (e.g., `WHERE DO THEY COME FROM?`)
2. Slide header strip (year, `PILOT.COM`, `CONFIDENTIAL`)
3. Slide footer strip (`PROJECT ADD PROJECT NAME`, `DATE APRIL 2026`)
4. Attribution lines in quotes

**Never use Space Mono for body paragraphs, titles, or bullets.**

---

## 6. Slide Chrome (Header + Footer)

Every non-cover slide has consistent chrome:

### Header Strip (top ~4% of slide)
| Position | Content | Style |
|----------|---------|-------|
| Top-left | `2026` (or current year) | Space Mono, ~10pt, muted purple `#8258EB` or `#DECEFF` |
| Top-right | `PILOT.COM` or `CONFIDENTIAL` | Space Mono, ~10pt, same muted color |

### Footer Strip (bottom ~8% of slide)
| Position | Content | Style |
|----------|---------|-------|
| Bottom-left | `PROJECT ADD PROJECT NAME` | Space Mono, ~10pt, muted `#8258EB` |
| Bottom-center-left | `DATE APRIL 2026` | Space Mono, ~10pt, muted (only on some slides) |
| Bottom-right | Pilot `p` icon mark | Small, muted — use actual logo mark |
| Very bottom edge | Thin bar | Solid `#5931DC` or `#DECEFF`, ~4px height |

---

## 7. Cards & Containers

When content is wrapped in a card (Layouts 7, 8, some elements in Layout 6):

- **Corner radius:** `16–24px`
- **Background:** White `#FFFFFF`
- **Drop shadow:** Optional — very subtle, purple-family only. `box-shadow: 0 4px 24px rgba(89,49,220,0.10)`
- **Internal padding:** ~24–32px on all sides
- **Card sits inset** from the slide edge — never bleeds to the edge

---

## 8. Charts & Data Visualization

All charts use the Pilot purple palette only. Do not use red/green for negative/positive.

| Chart Element | Color |
|---------------|-------|
| Primary bars/lines | `#5931DC` (Pilot Purple) |
| Secondary series | `#8258EB` (Brilliant) |
| Tertiary series | `#DECEFF` (Highlight) |
| Grid lines | Light gray `#E0E0E0` |
| Axis text | `#3F3C3D` (Pilot Black) |
| Data labels | `#5931DC` or `#3F3C3D` |
| Chart background | White card on lavender slide background |

---

## 9. Dos and Don'ts

### ✅ DO
- Use bold + light weight mix for all two-part headlines
- Left-align all text in content slides
- Use Space Mono only for metadata/labels/eyebrows
- Use white cards to contain screenshots and external content
- Use the light lavender background (`#F8EDFF`) for screenshot-heavy slides
- Apply the thin purple bottom bar on every non-cover slide
- Use numbered circles (①②③) or arrow bullets (→) instead of standard bullet points
- Keep the left panel of split slides spacious — only a headline, no body copy clutter

### ❌ DON'T
- Center text on any content slide
- Use red or green for data (stick to purple palette)
- Mix multiple accent colors on one slide
- Use vibrant accents (`#FFD967`, `#F891FF`, `#88ECFF`) as backgrounds
- Put more than one "hero message" per slide — one idea per slide
- Use italic type (not a Pilot slide convention)
- Place text on gradient backgrounds (only use gradient for cover/section slides with
  logo/wordmark, not for readable body copy)
- Use drop shadows that are not purple-family

---

## 10. Quick Reference: Layout → Use Case

| Layout | Name | Use When |
|--------|------|----------|
| 1 | Cover / Event | Opening or closing slides |
| 2 | Section Divider | New agenda section — one word |
| 3 | Section Title (oversized) | Introducing a new topic with a short framing phrase |
| 4 | Split Light / Dark | Frame + numbered/bulleted supporting points |
| 5 | Split Light / Light Purple | Frame + chart or data table |
| 6 | Framework Diagram | Architecture, org charts, process maps |
| 7 | Left Label + Right Card | Frame + single data asset in a card |
| 8 | Full-Bleed Screenshot | Real artifact: Slack, email, UI screenshot |
| 9 | Statement | Single provocative sentence, loads of whitespace |
| 10 | Quote | External quote or attribution |
| 11 | Agenda | Table of contents only |
