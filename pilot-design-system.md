# Pilot.com Design System Reference

> **Last updated:** April 2026  
> Extracted from https://www.pilot.com and the official Pilot Brand & Marketing Design System document.  
> Source CSS: `pilot-v2.shared.71c89cc4c.min.css` (cdn.prod.website-files.com) and `build.css` (assets.pilot.com)  
> Platform: Webflow + custom CSS + Marketo forms + Swiper.js carousels

## Quick Reference

| Category | Key Values |
|----------|-----------|
| Primary color | `#5931DC` (PILOT purple) |
| Body font | Euclid Circular B |
| Tech font | Space Mono (sparingly) |
| Human accent font | La Belle Aurore (≤4 words) |
| CTA border-radius | `999px` (full pill) |
| Text alignment | Left only — never centered |
| Drop shadow color | Purple family only, blur 50–100, opacity 10–20% |
| Container max-width | `75.5rem` (1208px) |
| Base text color | `#3f3c3d` |

---

## 1. CSS Custom Properties (`:root` Variables)

All variables are defined in `:root` and used throughout the Webflow CSS:

```css
:root {
  /* Core Brand Colors */
  --pilot-black:               #3f3c3d;
  --pilot-dark-purple:         #281350;
  --white:                     white;

  /* Purple Scale */
  --purple--1-primary-ee5:     #5f2ee5;   /* Primary CTA purple */
  --purple--2-beb:             #825beb;   /* Medium purple */
  --purple--3-30-6fc:          #c8b6fc;   /* Light purple */
  --purple--x-d89:             #3c2d89;   /* Deep purple / dark accent */
  --purple--x-c70:             #473c70;   /* Muted dark purple */
  --purple--3-cfd:             #f0ecfd;   /* Very light purple tint */

  /* Light / Background Colors */
  --light--light-5fa:          #f3f5fa;   /* Primary page background tint */
  --light--purple-f2edff:      #f2edff;
  --light--f8f8f8:             #f8f8f8;
  --light--blue-gray-afc:      #f9fafc;
  --light--light-ef5:          #edeef5;
  --light--light-purple-afd:   #e3dafd;
  --gray:                      #f3f5fa;
  --gray-999:                  #999;
  --gray-light:                #e0e0e0;
  --dark-gray-363:             #656363;
  --pale-periwinkle:           #f6f3ff;
  --transparent:               #fff0;

  /* Functional Colors */
  --bright-blue:               #4f9bf3;
  --cta-green:                 #47bfa4;
  --error-red:                 #ce1836;
  --supernova:                 #ffcc00;

  /* Accent / Illustrative Colors */
  --light-yellow:              #fee17f;
  --pilot-pink:                #f891ff;
  --pilot-pink-10:             #f891ff1a;  /* Pink at 10% opacity */
  --pilot-cyan:                #e7f9ff;
  --pale-lavender:             #fef4ff;
  --buttery-cream:             #fcf3d6;
  --pastel-violet:             #fbedff;
  --olive-green:               #6e9605;
}
```

---

## 2. Typography

### Font Families

Three primary font families are used, all self-hosted via Webflow CDN:

#### Primary: Euclid Circular B
The main brand/UI font. Used for headings, body text, and UI elements.

```css
@font-face {
  font-family: 'Euclid Circular B';
  src: url('...EuclidCircularB-Light-WebS.woff2') format('woff2');
  font-weight: 300;
}
@font-face {
  font-family: 'Euclid Circular B';
  src: url('...EuclidCircularB-Regular-WebS.woff2') format('woff2');
  font-weight: 400;
}
@font-face {
  font-family: 'Euclid Circular B';
  src: url('...EuclidCircularB-Medium-WebS.woff2') format('woff2');
  font-weight: 500;
}
@font-face {
  font-family: 'Euclid Circular B';
  src: url('...EuclidCircularB-Semibold-WebS.woff2') format('woff2');
  font-weight: 600;
}
@font-face {
  font-family: 'Euclid Circular B';
  src: url('...EuclidCircularB-Bold-WebS.woff2') format('woff2');
  font-weight: 700;
}
```

Webflow also uses shorthand aliases for this font:
- `font-family: Euclid, sans-serif` — used in headings, body, footer titles
- `font-family: Euclidcircularb Webs, sans-serif` — used in hero form

#### Secondary: Space Mono
Monospace font used for CTA buttons, labels, eyebrows, pricing tabs, and footer legal text.

```css
@font-face {
  font-family: 'Spacemono';
  src: url('...SpaceMono-Regular.ttf') format('truetype');
  font-weight: 400;
}
@font-face {
  font-family: 'Spacemono';
  src: url('...SpaceMono-Bold.ttf') format('truetype');
  font-weight: 700;
}
@font-face {
  font-family: 'Spacemono';
  src: url('...SpaceMono-Italic.ttf') format('truetype');
  font-weight: 400;
  font-style: italic;
}
@font-face {
  font-family: 'Spacemono';
  src: url('...SpaceMono-BoldItalic.ttf') format('truetype');
  font-weight: 700;
  font-style: italic;
}
```

Also referenced as `Space Mono` (the Google Fonts name).

#### Accent: La Belle Aurore
Decorative script/cursive font. Used for brand accent text (e.g., `.home_cursive` class).

```css
/* Loaded via WebFont.load({ google: { families: ["La Belle Aurore:300,400,500,600,700"] } }) */
font-family: 'La Belle Aurore', sans-serif;
```

Usage: `.home_cursive` — color: `#281350`, font-size: `2.5rem`, font-weight: `400`, letter-spacing: `-0.03em`, line-height: `1`.

---

### Base Typography

```css
body {
  font-family: Euclid, sans-serif;
  font-size: 16px;
  line-height: 1.5;
  color: var(--pilot-black); /* #3f3c3d */
  -webkit-font-smoothing: antialiased;
}

p {
  margin-top: 0;
  margin-bottom: 20px;
  font-size: 1rem;         /* 16px */
  line-height: 1.75rem;    /* 28px */
}
```

---

### Heading Scale (Webflow Defaults → Pilot Overrides)

| Element | Font Size     | Font Weight | Line Height | Font Family        |
|---------|---------------|-------------|-------------|--------------------|
| `h1`    | `3rem` (48px) | `600`       | `115%`      | Euclid, sans-serif |
| `h2`    | `2.5rem` (40px) | `600`     | `115%`      | Euclid, sans-serif |
| `h3`    | `2rem` (32px) | `600`       | `125%`      | Euclid, sans-serif |
| `h4`    | `1.5rem` (24px) | `600`     | `125%`      | Euclid, sans-serif |
| `h5`    | `1.25rem` (20px) | `600`    | `110%`      | —                  |
| `h6`    | `1rem` (16px) | `600`       | `120%`      | —                  |

Webflow default fallbacks (before overrides):
| Element | Font Size | Line Height |
|---------|-----------|-------------|
| `h1`    | 38px      | 44px        |
| `h2`    | 32px      | 36px        |
| `h3`    | 24px      | 30px        |
| `h4`    | 18px      | 24px        |
| `h5`    | 14px      | 20px        |
| `h6`    | 12px      | 18px        |

---

### Typography Utility Classes

```css
.heading-large   { font-size: 3rem;    font-weight: 600; line-height: 3.6rem; }
.heading-medium  { font-size: 2rem;    font-weight: 600; line-height: 2.2rem; }
.heading-small   { font-size: 1.5rem;  font-weight: 600; line-height: 2rem; }

.text-large         { font-size: 1.25rem;  line-height: 2rem; }
.text-semibold      { font-size: 1rem;     font-weight: 600; line-height: 1.6rem; }
.text-1rem          { font-size: 1rem;     line-height: 1.5rem; }
.text-extra-large   { font-size: 2rem;     line-height: 2.8rem; }
.text-extra-space   { line-height: 2; }
.text-leading-1-8rem { line-height: 1.8rem; }

.text-color-purple      { color: var(--purple--1-primary-ee5); }
.text-color-dark-purple { color: var(--purple--x-d89); }
.text-purple-dark       { color: var(--purple--x-d89); }
.text-lighter           { color: #656363; }
.text-center            { text-align: center; }
.text-align-center      { text-align: center; }
.text-link-purple-underline { text-decoration: underline; text-underline-offset: 10px; }
```

---

### Font Weight Scale

| Weight | Usage |
|--------|-------|
| `300`  | Light text, Euclid Circular B Light |
| `400`  | Body text, regular weight |
| `500`  | Medium emphasis |
| `600`  | Headings, semibold CTAs, nav items |
| `700`  | Bold, strong emphasis |
| `900`  | Rare / heavy use |

---

### Font Size Scale (pixel equivalents, base 16px)

| rem Value | px Equivalent | Usage |
|-----------|---------------|-------|
| `0.75rem`  | 12px | Small labels, eyebrows, legal text |
| `0.875rem` | 14px | Small body text |
| `1rem`     | 16px | Base body text |
| `1.125rem` | 18px | Hero form, select inputs |
| `1.25rem`  | 20px | Footer titles, large body |
| `1.5rem`   | 24px | H4, card headers |
| `1.75rem`  | 28px | Medium headings |
| `2rem`     | 32px | H3, `.heading-medium` |
| `2.5rem`   | 40px | H2, cursive accent |
| `3rem`     | 48px | H1, `.heading-large` |
| `3.5rem`   | 56px | Large display |
| `4rem`     | 64px | XL display |
| `5rem`     | 80px | Hero display |

---

## 3. Color System

### Brand Color Palette

| Name | CSS Variable | Hex | Usage |
|------|-------------|-----|-------|
| **Pilot Purple** (Primary) | `--purple--1-primary-ee5` | `#5f2ee5` | CTA buttons, links, primary accents, borders |
| **Pilot Black** | `--pilot-black` | `#3f3c3d` | Body text, default text color |
| **Pilot Dark Purple** | `--pilot-dark-purple` | `#281350` | Dark backgrounds, cursive text, hero text |
| **White** | `--white` | `#ffffff` | Backgrounds, button text on dark |
| **Deep Purple** | `--purple--x-d89` | `#3c2d89` | Testimonial quote marks, dark accents, footer nav links |
| **Deep Purple (alt)** | `--purple--x-c70` | `#473c70` | Text dividers |
| **Medium Purple** | `--purple--2-beb` | `#825beb` | Secondary purple |
| **Light Purple** | `--purple--3-30-6fc` | `#c8b6fc` | Nav banner text, light accents |

### Extended Purple Scale

| Hex | Usage |
|-----|-------|
| `#5931dc` | Slide CTA button background, slightly darker than primary |
| `#6a46df` | Hover/active states |
| `#3c2d89` | Dark accent, quote marks |
| `#322a4e` | Very dark purple |
| `#3e2b62` | Hero section border color |
| `#e3dafd` | `--light--light-purple-afd` — light purple backgrounds |
| `#f0ecfd` | `--purple--3-cfd` — very light purple tint |
| `#f2edff` | `--light--purple-f2edff` — near-white purple tint |
| `#f6f3ff` | `--pale-periwinkle` — ultra-light purple background |

### Neutral / Gray Scale

| Name | CSS Variable | Hex | Usage |
|------|-------------|-----|-------|
| Near-black | — | `#1a1b1f` | Dark text variant |
| Body text | `--pilot-black` | `#3f3c3d` | Default text |
| Dark gray | `--dark-gray-363` | `#656363` | Secondary text, nav links |
| Medium gray | `--gray-999` | `#999` | Placeholder text, muted UI |
| Light gray (border) | `--gray-light` | `#e0e0e0` | Input borders, dividers, card borders |
| Light background | `--light--light-5fa` | `#f3f5fa` | Section backgrounds |
| Lighter background | `--light--f8f8f8` | `#f8f8f8` | Card backgrounds |
| Lightest background | `--light--blue-gray-afc` | `#f9fafc` | Partner sections |
| Off-white | — | `#fafafa` | Card backgrounds |

### Functional Colors

| Name | CSS Variable | Hex | Usage |
|------|-------------|-----|-------|
| Error Red | `--error-red` | `#ce1836` | Form validation errors · **Product only — not for marketing** |
| CTA Green | `--cta-green` | `#47bfa4` | Green CTA links · **Product only — not for marketing** |
| Teal/Aqua | — | `#3da291` | Accent color |
| Bright Blue | `--bright-blue` | `#4f9bf3` | Informational blue |
| Supernova Yellow | `--supernova` | `#ffcc00` | Attention/highlight |
| Olive Green | `--olive-green` | `#6e9605` | Growth eyebrow labels |

### Illustrative / Accent Colors

| Name | CSS Variable | Hex | Usage |
|------|-------------|-----|-------|
| Pilot Pink | `--pilot-pink` | `#f891ff` | Gradient accents, chat image border |
| Pilot Cyan | `--pilot-cyan` | `#e7f9ff` | Background tint |
| Pale Lavender | `--pale-lavender` | `#fef4ff` | Pricing card footer background |
| Buttery Cream | `--buttery-cream` | `#fcf3d6` | Warm accent |
| Pastel Violet | `--pastel-violet` | `#fbedff` | Light purple tint |
| Light Yellow | `--light-yellow` | `#fee17f` | Highlight backgrounds |
| Lime/Growth | — | `#f3ffd3` | Growth section card gradient |
| Gold/Amber | — | `#967000` | Growth eyebrow text color |

### Alpha / Opacity Variants

| Hex | Base Color | Opacity | Usage |
|-----|-----------|---------|-------|
| `#c8b6fc1a` | Purple-3 | ~10% | CTA button border gradient |
| `#5931dc1a` | Purple CTA | ~10% | CTA button border gradient |
| `#5f2ee51a` | Primary purple | ~10% | Shadow glow |
| `#3c2d890d` | Deep purple | ~5% | Subtle backgrounds |
| `#3c2d8914` | Deep purple | ~8% | |
| `#3c2d891a` | Deep purple | ~10% | |
| `#281350 at 5%` | Dark purple | ~5% | Section backgrounds |
| `#f891ff1a` | Pink | ~10% | `--pilot-pink-10` |

---

## 4. Border Radius

| Value | Usage |
|-------|-------|
| `4px` | Buttons (`.button`), form checkboxes, dropdown dates, small cards |
| `6px` | Range track |
| `8px` | Cards (Chilipiper modal) |
| `12px` | Small cards |
| `16px` | Chat/message images |
| `20px` / `20px 20px 60px` | Section shapes |
| `1rem` (16px) | Card `.card-rounded`, `.cta` section |
| `0.5rem` (8px) | `.card-white`, `.card-gray` |
| `0.75rem` (12px) | Nav mega-menu icon links |
| `1.5rem` (24px) | Medium pill-shaped elements |
| `2rem` (32px) | Larger pills |
| `2.875rem` | `.home_form-cta` (hero CTA button) |
| `3rem` | `.home_slide-btn` (slide CTA button) |
| `3.5rem` | `.home_form-wrap` (hero email form container) |
| `50%` | Circular elements |
| `50px` | Pill buttons |
| `60px` | Pricing tab menu |
| `100px` | Fully rounded large pills |
| `999px` | Infinite radius (always pill) |
| `100%` | Perfect circles |

---

## 5. Spacing System

### Container / Layout Widths

| Class | Max Width | H-Padding |
|-------|-----------|-----------|
| `.container` | `75.5rem` (1208px) | `40px` |
| `.container-narrow` | `856px` | `40px` |
| `.container-narrower` | `766px` | `40px` |
| `.container-max-width-836px` | `836px` | — |
| `.container-max-width-1080px` | `1080px` | — |
| `.container-max-85rem` | `85rem` (1360px) | — |
| `.container-max-width-72-5rem` | `72.5rem` | — |
| `.container-max-width-1222` | `1222px` | — |
| `.container-max-80rem` | `80rem` (1280px) | — |

### Section Padding Patterns

| Class / Pattern | Padding |
|----------------|---------|
| `.section-hero-base` | `7.5rem` top/bottom |
| Standard section | `120px` top/bottom |
| Large section gap | `160px` top |
| XL section gap | `200px` top |
| `.padding-top-7-5rem` | `7.5rem` top |
| `.padding-top-6rem` | `6rem` top |
| `.padding-top-5rem` | `5rem` top |
| `.padding-bottom-5rem` | `5rem` bottom |
| `.padding-bottom-240px` | `240px` bottom |
| `.padding-bottom-22rem` | `22rem` bottom |
| `.padding-tb-5rem` | `5rem` top + bottom |
| `.padding-9rem-6-5rem` | `7.5rem` top + bottom |
| `.footer` | `5rem` top, `2rem` bottom |

### Margin Utilities

| Class | Value |
|-------|-------|
| `.margin-bottom-0` | `margin-bottom: 0` |
| `.margin-bottom-small` | `40px` |
| `.margin-bottom-medium` | `24–40px` (responsive) |
| `.margin-bottom-xlarge` | `3rem` / `font-size: 3rem` |
| `.margin-bottom-xxlarge` | `100px` |
| `.margin-bottom-60px` | `60px` |
| `.margin-bottom-3-75rem` | `3.75rem` |
| `.margin-top-0` | `0` |
| `.margin-top-5rem` | `5rem` |
| `.margin-top-3rem` | display inline-block |
| `.margin-negative-8rem` | `margin-top: -8rem` |

### Grid System

```css
/* Default Webflow grid */
.w-layout-grid {
  grid-row-gap: 16px;
  grid-column-gap: 16px;
  grid-template-rows: auto auto;
  grid-template-columns: 1fr 1fr;
  grid-auto-columns: 1fr;
  display: grid;
}

/* Utility grids */
.grid-2col  { grid-template-columns: 1fr 1fr;         column-gap: 3.75rem; }
.grid-3-col { grid-template-columns: 1fr 1fr 1fr;     gap: 16px; }
.grid-5-col { grid-template-columns: 1fr 1fr 1fr 1fr 1fr; gap: 16px; }
.grid__3    { grid-template-columns: 1fr 1fr 1fr; }
.grid__4    { grid-template-columns: 1fr 1fr 1fr 1fr; }
.grid-quotes { grid-template-columns: 1fr 1fr 1fr; column-gap: 40px; row-gap: 30px; }
.pricing-columns { grid-template-columns: 1fr 1fr; column-gap: 40px; }
.footer-grid     { grid-template-columns: 1fr 1fr 1fr 1fr 1fr; column-gap: 3rem; }
```

---

## 6. Button Styles

### Primary CTA Button (hero email form)

```css
.home_form-cta {
  background-color: var(--purple--1-primary-ee5); /* #5f2ee5 */
  color: var(--white);
  text-transform: uppercase;
  border-radius: 2.875rem;
  padding: 0.9375rem 1.5rem;
  font-family: Spacemono, sans-serif;
  line-height: 1;
}
```

### Standard Button (outlined)

```css
.button {
  border: 1px solid var(--purple--1-primary-ee5);
  color: var(--purple--1-primary-ee5);
  background-color: transparent;
  border-radius: 4px;
  padding: 8px 32px;
  text-align: center;
  white-space: nowrap;
  cursor: pointer;
  transition: all 0.2s;
  position: relative;
}

.btn-text-white {
  border-color: var(--white);
  color: var(--white);
}
```

### Slide/Carousel CTA Button

```css
.home_slide-btn {
  background-color: #5931dc;
  color: white;
  text-transform: uppercase;
  letter-spacing: -0.03em;
  border-radius: 3rem;
  padding: 0.75rem 1.25rem;
  font-family: Spacemono, sans-serif;
  line-height: 1;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  gap: 0.5rem;
}
```

### CTA Section Container

```css
.cta {
  background-color: var(--pilot-dark-purple); /* #281350 */
  color: var(--white);
  border-radius: 1rem;
  padding: 5rem 6rem;
  /* Responsive: 3rem 4rem → 2rem lr */
}
```

### Green CTA Link

```css
.cta-link {
  color: var(--cta-green); /* #47bfa4 */
  border-bottom: 1px solid transparent;
  padding-bottom: 6px;
  font-size: 1rem;
  line-height: 1.6rem;
  text-decoration: none;
}
```

### Button Height Helper

```css
.btn-height-3-5-rem {
  display: flex;
  align-items: center;
  justify-content: center;
  min-height: 3.5rem;
}
```

### Flex Button Row

```css
.btn_flex {
  display: flex;
  gap: 0.5rem;
  /* Mobile: flex-direction column; Desktop: row */
}

.home_btn-wrap {
  display: flex;
  gap: 1rem;
}
```

### Pricing Tab Button

```css
.pricing-tab__link {
  color: var(--purple--x-d89);
  text-align: center;
  background-color: transparent;
  border-radius: 60px;
  width: 100%;
  padding: 20px 35px;
  font-size: 24px;
  font-weight: 600;
  font-family: Spacemono, sans-serif;
}
```

---

## 7. Navigation

### Top-Level Nav Component

```css
.navbar7_component {
  z-index: 555;
  background-color: var(--white);
  width: 100%;
  position: fixed;
  top: 0;
  display: block;
  align-items: center;
  transition: box-shadow 0.3s ease;
}

.navbar7_component.scrolled {
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

.navbar7_container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 100%;
  max-width: 75.5rem;
  height: 100%;
  margin-left: auto;
  margin-right: auto;
  padding-left: 40px;
  padding-right: 40px;
}

.navbar7_menu {
  display: flex;
  flex: 1;
  justify-content: space-between;
  align-items: center;
  margin-left: 1.5rem;
  position: static;
}

.navbar7_link {
  color: var(--dark-gray-363);
  padding: 1.5rem 1rem;
  line-height: 1.6;
}

.navbar7_dropdown-toggle {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  color: var(--dark-gray-363);
  border-bottom: 2px solid var(--transparent);
  padding: 1.5rem 1rem;
}

.navbar7_menu-right {
  display: flex;
  align-items: center;
  gap: 1rem;
  grid-template-columns: 1fr 1fr;
}
```

### Nav Banner (top announcement bar)

```css
.nav-banner {
  background-color: var(--purple--x-d89); /* #3c2d89 */
  color: #fff;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 50px;
  font-size: 15px;
  font-weight: 600;
  transition: all 0.2s ease-in;
  position: relative;
}

.nav-banner_text-wrap {
  color: var(--purple--3-30-6fc); /* #c8b6fc */
}
```

### Mega Menu

```css
.nav-megamenu {
  grid-template-columns: 1fr 1fr 0.7fr;
  gap: 1rem;
  width: 100%;
}

.nav-mega-iconlink {
  display: flex;
  align-items: center;
  gap: 24px;
  background-color: transparent;
  color: var(--pilot-black);
  border-radius: 0.75rem;
  padding: 20px 24px;
  margin-bottom: 8px;
  transition-duration: 0.2s;
}

.nav-mega-left {
  border-right: 1px solid var(--gray-light);
  padding-right: 4rem;
}
```

### Legacy Nav (global-nav)

```css
.global-nav {
  z-index: 999990;
  background-color: transparent;
  margin-bottom: -80px;
  position: sticky;
  inset: 0 0% auto;
  transition: all 0.3s;
}

.global-nav-container {
  display: flex;
  align-items: center;
  height: 80px;
}

.global-nav-link {
  color: #656363;
  white-space: nowrap;
  margin-right: 30px;
  padding: 0;
}

.global-nav.floated {
  background: #fff;
  box-shadow: 0 16px 24px rgba(14, 13, 18, 0.07);
}
```

---

## 8. Section Patterns

### Hero Section

```css
/* Hero content wrapper */
.home_hero_content-wrap {
  width: 88%;
  max-width: 36.8125rem;
  margin-bottom: 6rem;
  min-width: auto;
}

/* Hero flex layout */
.home_hero_flex {
  display: flex;
  row-gap: 5rem;
}

/* Email capture form wrapper */
.home_form-wrap {
  background-color: var(--white);
  border-radius: 3.5rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 100%;
  max-width: 555px;
  min-height: 72px;
  padding: 0.375rem 0.75rem 0.375rem 1.5rem;
  font-family: Euclidcircularb Webs, sans-serif;
  font-size: 1.125rem;
}

/* Hero input field */
.home_input-field {
  color: #281350;
  border: 1px transparent;
  margin-bottom: 0;
  padding-left: 0;
  padding-right: 0;
  font-size: 1rem;
}

/* Hero product image */
.home_hero_image {
  z-index: 3;
  width: 96%;
  max-width: 35rem;
  margin-top: 6.4375rem;
  display: block;
  position: relative;
}
```

### Hero Headline Class

```css
.new_hero-headline {
  /* Applied to H1 */
  /* Uses heading styles: font-size: 3rem, font-weight: 600, line-height: 115% */
}
```

---

### About / Feature Section

```css
.home_about_flex {
  display: flex;
  column-gap: 5rem;
  row-gap: 5rem;
  position: relative;
  overflow: hidden;
}

.home_about_cards {
  display: flex;
  flex-flow: column;
  align-items: flex-start;
  width: 33.33%;
  padding: 3.5rem 1rem 3.5rem 1.5rem;
  gap: 2.5rem;
}

.home_about_card-wrap {
  display: flex;
  border-top: 1px solid #dae9f3;
  border-bottom: 1px solid #dae9f3;
  margin-bottom: 6.5625rem;
}
```

### CFO Section

```css
.home_cfo_flex {
  display: flex;
  border-top: 1px solid #e9e7ed;
  border-bottom: 1px solid #e9e7ed;
  margin-top: 6rem;
  margin-bottom: 5rem;
}

.home_cfo_flex_item {
  display: flex;
  flex-flow: column;
  justify-content: space-between;
  align-items: flex-start;
  min-width: 33.33%;
  padding: 1.5rem 0 0 1.5rem;
  background-image: linear-gradient(155deg, #f3ffd300 50%, #f3ffd3);
  position: relative;
}

.home_cfo_flex_item_header {
  background-color: #f3ffd3;  /* lime green accent */
  padding: 0.375rem;
  font-size: 1.5rem;
  line-height: 1;
  display: inline-block;
}
```

### Growth Section

```css
.home_growth-flex {
  display: flex;
  flex-flow: wrap;
  border-top: 1px solid #e7ddc9;
  margin-top: 2.5rem;
  margin-bottom: 5rem;
}

.home_growth-flex-card {
  flex: 1;
  min-width: 50%;
  border-bottom: 1px solid #e7ddc9;
  border-right: 1px solid #e7ddc9;
  padding-top: 1.5rem;
  padding-bottom: 12rem;
  padding-left: 0;
  position: relative;
}

.home_growth-flex-card-eyebrow {
  color: #967000;
  letter-spacing: 1.2px;
  text-transform: uppercase;
  border-left: 2px solid #967000;
  margin-bottom: 0.5rem;
  margin-left: -1px;
  padding-left: 1.5rem;
  font-size: 12px;
}
```

### Insights / Content Cards Section

```css
.home_insights-card {
  /* Card for resource/content links */
}

.home_slide-eyebrow {
  letter-spacing: 1.2px;
  text-transform: uppercase;
  font-size: 12px;
  font-weight: 600;
}

.home_slide-text-content {
  display: flex;
  flex-flow: column;
  flex: 1;
  padding-top: 3.5rem;
  padding-left: 3.5rem;
  padding-right: 4rem;
  background-color: var(--white);
}
```

---

## 9. Card Styles

```css
.card-large {
  background-color: #fff;
  border: 1px solid #e0e0e0;
  padding: 3.75rem;
}

.card-small {
  background-color: #fff;
  border: 1px solid #e0e0e0;
  border-radius: 4px;
  padding: 40px;
}

.card-rounded {
  border-radius: 1rem;
  padding: 36px;
}

.card-white {
  background-color: var(--white);
  border-radius: 0.5rem;
  width: 100%;
  padding: 4rem;
}

.card-gray {
  background-color: var(--light--light-5fa); /* #f3f5fa */
  border-radius: 0.5rem;
  width: 100%;
  padding: 4rem;
}

.card-gray-light {
  background-color: var(--light--f8f8f8); /* #f8f8f8 */
  padding: 2rem;
}
```

### Pricing Cards

```css
.pricing-card {
  background-color: #fff;
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  height: 100%;
  padding: 40px 30px;
}

.pricing-card-footer {
  background-color: var(--pale-lavender); /* #fef4ff */
  text-align: center;
  border-bottom: 1px solid #e0e0e0;
  border-left: 1px solid #e0e0e0;
  border-right: 1px solid #e0e0e0;
  min-height: 55px;
  margin: 40px -41px -41px;
  padding: 15px 40px;
  font-size: 15px;
}

.pricing-header {
  margin-bottom: 20px;
  font-size: 36px;
  line-height: 1.3em;
}

.pricing-tab__menu {
  background-color: #f3f5fa;
  border-radius: 60px;
  grid-template-columns: 1fr 1fr 1fr;
  max-width: 874px;
  margin: 0 auto 110px;
  padding: (none on self, button handles padding);
  font-family: Spacemono, sans-serif;
  display: grid;
}
```

---

## 10. Testimonial / Social Proof

```css
.testimonial::before {
  color: #3c2d89;
  content: "\201C";  /* opening curly quote */
  display: block;
  font-size: 60px;
  font-weight: 600;
  line-height: 45px;
}

/* Testimonial card rise animation */
@keyframes stand-out {
  0%   { box-shadow: none; transform: translateY(0); }
  6%   { box-shadow: 0 64px 46px rgba(0,0,0,0.04); transform: translateY(-60px); }
  33%  { box-shadow: 0 64px 46px rgba(0,0,0,0.04); transform: translateY(-60px); }
  39%  { box-shadow: none; transform: translateY(0); }
  100% { box-shadow: none; transform: translateY(0); }
}

.testimonial {
  animation: stand-out 12s infinite;
}
.testimonial:first-child { animation-delay: 8s; }
.testimonial:last-child  { animation-delay: 4s; }
```

---

## 11. Footer

```css
.footer {
  padding-top: 5rem;
  padding-bottom: 2rem;
}

.footer-grid {
  grid-template-columns: 1fr 1fr 1fr 1fr 1fr;
  column-gap: 3rem;
  row-gap: 3rem;
  /* Tablet: 1fr 1fr 1fr; Mobile: 1fr 1fr */
}

.footer__title {
  margin-bottom: 20px;
  font-family: Euclid, sans-serif;
  font-size: 20px;
  font-weight: 600;
}

.footer__link {
  color: var(--pilot-black);
  margin-bottom: 20px;
  text-decoration: none;
  display: block;
}

.footer__lower {
  color: var(--gray-999);
  padding-top: 40px;
  font-family: Spacemono, sans-serif;
  font-size: 13px;
  line-height: 24px;
  display: flex;
}

.footer__lower-link {
  color: var(--pilot-dark-purple);
  margin-left: 40px;
  font-family: Spacemono, sans-serif;
  text-decoration: none;
}
```

### New Footer Cards (Bottom CTA section)

```css
.new_footer-card    { /* Individual footer CTA cards */ }
.new_footer-flex    { /* Flex container for footer CTAs */ }

/* Footer card color variants */
.new_footer_lavender-box { background related to pale-lavender }
.new_footer_purple-box   { background related to dark purple }
```

---

## 12. Forms & Inputs

```css
/* Base select/input styling */
.nice-select,
.w-select {
  display: flex;
  align-items: center;
  background-color: #fff;
  border: 1px solid #e0e0e0;
  border-radius: 3px;
  font-size: 18px;
  min-height: 60px;
  padding: 15px;
  transition: 0.3s;
}

.nice-select:hover,
.w-select:hover {
  border: 1px solid #5f2ee5;
  cursor: pointer;
}

.nice-select:active,
.nice-select:focus,
.w-select:active,
.w-select:focus {
  border: 1px solid #5f2ee5;
  outline: none;
}

/* Form input focus (email hero form) */
.mktoFormRow input:focus {
  outline: none;
  border: 1px solid #5f2ee5;
}

/* Select dropdown list */
.nice-select .list {
  background-color: #fff;
  border: 1px solid #e0e0e0;
  border-radius: 2px;
  box-shadow: 0 7px 20px 0 rgba(68, 68, 68, 0.11);
  font-size: 18px;
}

/* Checkbox styling */
.mktoCheckboxList input + label::before {
  background: #fff;
  border: 1px solid #e0e0e0;
  border-radius: 4px;
  width: 13px;
  height: 13px;
}
```

---

## 13. Shadow / Elevation Scale

| Usage | Value |
|-------|-------|
| Nav scroll shadow | `0 4px 8px rgba(0,0,0,0.1)` |
| Floated nav shadow | `0 16px 24px rgba(14,13,18,0.07)` |
| Card hover shadow | `0 16px 35px #0000001a` |
| Deep card shadow | `0 16px 35px #0000001a, 0 63px 63px #00000017, 0 142px 85px #0000000d` |
| Dropdown shadow | `0 7px 20px 0 rgba(68,68,68,0.11)` |
| Inner glow | `0 0 0 1px rgba(0,0,0,0.1)` |
| Purple glow | `0 0 3px 0 var(--purple--1-primary-ee5), 0 8px 16px 0 #6008b514` |
| Dark purple glow | `0 0 60px #3c2d8980` |
| Subtle card | `-1px 8px 16px #3e3c3d14, 0 0 1px #65636229` |
| Testimonial lift | `0 64px 46px rgba(0,0,0,0.04)` |

---

## 14. Transitions & Animations

```css
/* Standard transitions */
transition: all 0.2s;
transition: all 0.3s;
transition: all 0.5s;
transition: all 0.3s cubic-bezier(0.455, 0.03, 0.515, 0.955);
transition: background-color 0.1s, color 0.1s;
transition: background-color 0.2s;
transition: color 0.2s, background-color 0.2s;
transition: transform 0.2s;
transition: opacity 0.15s;
transition: height 0.5s;

/* Logo wall infinite scroll */
@keyframes moveLogoWall {
  to { transform: translateX(-2872px); }
}
.logo-carousel-flex {
  animation: moveLogoWall 125s linear infinite;
}

/* Testimonial card float animation */
@keyframes stand-out {
  0%, 39%, 100% { box-shadow: none; transform: translateY(0); }
  6%, 33%       { box-shadow: 0 64px 46px rgba(0,0,0,0.04); transform: translateY(-60px); }
}
```

---

## 15. Letter Spacing Values

| Value | Usage |
|-------|-------|
| `letter-spacing: -0.03em` | Cursive accent text, slide CTA buttons |
| `letter-spacing: -0.01em` | Tight headings |
| `letter-spacing: 0` | Reset |
| `letter-spacing: 1.2px` | Eyebrow labels (uppercase small caps) |
| `letter-spacing: 1.92px` | Uppercase labels |
| `letter-spacing: 2px` | Button text (uppercase) |
| `letter-spacing: 0.1rem` | Moderate spacing |
| `letter-spacing: 0.15em` | Wide caps |
| `letter-spacing: 0.16em` | Tracking |

---

## 16. Responsive Breakpoints

| Breakpoint | CSS Media Query | Usage |
|-----------|----------------|-------|
| Mobile | `max-width: 479px` | Single column, stacked layout |
| Tablet | `max-width: 767px` | 2 column, simplified nav |
| Medium | `min-width: 768px` | Table hover effects enabled |
| Desktop | `min-width: 1281px` | Nav container padding adjustment |
| Large | `min-width: 1900px` | Hero image shadow hidden |

Webflow collapse breakpoint: `medium` (768px) — mobile menu activates below this.

---

## 17. Page Sections Summary

The homepage (`/`) is a Webflow-built page with these major sections in order:

| Section | Class | Background | Key Feature |
|---------|-------|-----------|-------------|
| **Announcement Banner** | `.navbanner` | `#3c2d89` (deep purple) | White text on purple |
| **Navigation** | `.navbar7_component` | `#ffffff` | Sticky, shadow on scroll |
| **Hero** | `.new_hero` | White/light gradient | Email capture + dashboard image |
| **Social Proof Logos** | logo carousel | White | Trusted by 3,000+ clients |
| **About / Features** | `.home_about_flex` | White with `#dae9f3` borders | 3-column feature cards |
| **AI Dashboard** | `.home_ai_*` | White | AI financial insights demo |
| **CFO Guidance** | `.home_cfo_flex` | White + `#f3ffd3` (lime) accents | 3 advisor profiles |
| **Growth Scenarios** | `.home_growth-flex` | White with `#e7ddc9` borders | 4 use case cards |
| **Case Studies** | Swiper slider | White | Rotating customer stories |
| **Resources** | `.home_insights-*` | White | 4 resource/guide cards |
| **3-Way CTA** | `.new_footer-*` | Light purple + dark purple | Conversion section |
| **Footer** | `.footer` | White | 5-column link grid |

---

## 18. Utility Class Patterns

### Display / Visibility

```css
.shown       { display: block; }
.no-animation { animation: none !important; }
.full-screen  { overflow-y: scroll; width: 100%; }
```

### Justify / Alignment

```css
.flex-center-vertically  { display: flex; justify-content: center; align-items: center; }
.flex-stacked            { display: flex; flex-direction: column; justify-content: space-between; }
.flex-justify-space-btw  { display: flex; flex-direction: column; justify-content: space-between; align-items: flex-start; }
.justify-space-btw       { (flex justify-content: space-between) }
.flex-space-evenly       { justify-content: space-around; }
.flex-end                { align-items: flex-end; }
```

### Width Constraints

```css
.max-width-31rem    { max-width: 31rem; }
.max-width-full-tablet { /* full width at tablet */ }
.section-heading    { text-align: center; max-width: 900px; margin: 0 auto 3rem; }
.pricing__2-col-max-width { max-width: 900px; margin: auto; }
```

### Text Decorative

```css
.home_text-underline   { /* brand underline accent */ }
.home_mono-text-link   { font-family: Spacemono; /* monospace link */ }
.svg-divider           { fill: currentColor; }
```

---

## 19. Third-Party Integrations

| Tool | Purpose | ID / Key |
|------|---------|----------|
| **Webflow** | CMS/hosting platform | Site ID: `60a5136f2c6c8e4fb3a130d9` |
| **Google Tag Manager** | Analytics orchestration | `GTM-WCT3V3Z`, `GTM-KWQ5QTCZ` |
| **Marketo** | Lead forms | Account: `754-NWB-621` |
| **Intellimize** | A/B testing / personalization | `117814141` |
| **Convert** | A/B testing | `10043185-10044507` |
| **Chili Piper** | Meeting scheduling | Styled to match brand (`#5f2ee5`) |
| **OneTrust** | Cookie consent | `1abf67ec-40bb-420e-95f6-8625a5eaf16b` |
| **Swiper.js** | Carousels / sliders | `swiper-bundle.min.css/js` (CDN jsdelivr) |
| **GSAP 3** | Animations | `gsap.min.js` (cdnjs, v3.12.2) |
| **jQuery** | DOM manipulation | `jquery-3.5.1.min.js` |
| **Munchkin (Marketo)** | Tracking | `munchkin.marketo.net` |
| **Bizible** | Attribution | `cdn.bizible.com/scripts/bizible.js` |
| **OptinMonster** | Lead gen popups | Account `64522`, User `57229` |

---

## 20. Logo Assets

| Asset | URL |
|-------|-----|
| Pilot logo (SVG, current) | `https://cdn.prod.website-files.com/60a5136f2c6c8e4fb3a130d9/6876671c627d80dce661a525_Pilot.svg` |
| Pilot logo (black) | `https://cdn.prod.website-files.com/60a5136f2c6c8e4fb3a130d9/60a6655502236d57ba0dc64f_pilot-logo-black.svg` |
| Logo dimensions | `width: 65px, height: 35px` |

### Media Kit

The complete media kit — including all logo variants (full logo, lettermark) in SVG, PNG, and PDF formats — is maintained in Google Drive:

**[→ Pilot Media Kit (Google Drive)](https://drive.google.com/drive/folders/1h5BirEATWxpMydrbScK5M-YV8zKhRJmP)**

Available formats and variants:

| Variant | Colorways |
|---------|-----------|
| **Full logo** | Black, Purple, Purple Fill, White, White Fill |
| **Lettermark** | Black, Purple, Purple Fill, White, White Fill |

Formats: SVG, PNG, PDF. Download-ready `.zip` archives are also available in the Drive folder.

---

## 21. Key Design Patterns Summary

### Color Usage Rules
- **Purple `#5f2ee5`**: All primary CTAs, link hover states, form focus borders, selected states
- **Dark Purple `#281350`**: Dark section backgrounds, input text, strong brand moments
- **`#3c2d89`**: Secondary dark accents, testimonial marks, deep purple sections
- **`#f3f5fa`**: Standard light section background
- **`#f9fafc`**: Partner/trust section background (slightly blue-tinted)
- **White `#ffffff`**: Default card and page background

### Typographic Hierarchy Rules
- **Display/H1**: Euclid Circular B, 3rem, 600 weight, 115% line-height
- **Section headers/H2**: Euclid Circular B, 2.5rem, 600 weight, 115% line-height
- **Card headers/H3**: Euclid Circular B, 2rem, 600 weight, 125% line-height
- **Body text**: Euclid Circular B, 1rem (16px), 400 weight, 1.75rem line-height
- **Buttons/Labels/Eyebrows**: Space Mono, uppercase, letter-spacing 1.2–2px
- **Accent/Cursive**: La Belle Aurore, 2.5rem, `#281350`

### Button Rules
- **Primary filled**: `#5f2ee5` background, white text, `Spacemono`, uppercase, `border-radius: 2.875rem`
- **Secondary outlined**: `1px solid #5f2ee5`, `#5f2ee5` text, `border-radius: 4px`
- **White outlined**: `1px solid white`, white text (for dark backgrounds)
- **All buttons**: `transition: all 0.2s`, `cursor: pointer`, `white-space: nowrap`

### Spacing Rules
- **Section vertical padding**: 120px standard, 7.5rem (120px) hero
- **Container max-width**: `75.5rem` (1208px) standard
- **Grid gaps**: 16px default, 40px for pricing, 3rem for footer
- **Card padding**: 40px standard, 4rem larger cards

---

## 22. Brand Philosophy: People & Tech Spectrum

Pilot is 50% people, 50% tech. This ratio shifts depending on context:

| Situation | Ratio | Visual Direction |
|-----------|-------|-----------------|
| CFOs building a financial model | **80% people** | Lead with photography, human warmth, soft colors |
| Day-to-day bookkeeping | **50/50** | Balance product UI + human imagery |
| AI accounting offering | **80% tech** | Lead with product screenshots, data, precision visuals |

**Rule:** Match your visual choices (photos, illustrations, UI screenshots) to where the feature/service sits on this spectrum. The more human the situation, the more you lead with people photography, the La Belle Aurore accent font, and warm background colors. The more technical, the more you lead with product UI, Space Mono typography, and precise grid/data backgrounds.

```
MORE PEOPLE  •————————————————  HALF AND HALF  ————————————————•  MORE SOFTWARE
   (photos, warmth,                (mixed)                 (product UI, data,
   La Belle Aurore)                                         Space Mono, precision)
```

---

## 23. Official Brand Color Palette (Named Colors)

These are the official named colors from the Pilot brand system. Use these names when communicating about brand colors internally.

### Primary Purple Scale

| Name | Hex | CSS Variable | Usage |
|------|-----|-------------|-------|
| **PROFIT** | `#281350` | `--pilot-dark-purple` | Darkest purple; dark backgrounds, deep anchors. **Note: Too dark for profit-related positive messaging.** |
| **PILOT** | `#5931DC` | `--purple--1-primary-ee5` (≈) | Primary brand purple; all CTAs, key links, primary accents |
| **BRILLIANT** | `#825BEB` | `--purple--2-beb` | Medium purple; secondary accents, gradients |
| **HIGHLIGHT** | `#DECEFF` | — | Light purple; the same highlight color used in the Pilot product — creates uniformity across materials. Signals a value has changed. |
| **MARGIN** | `#F6F3FF` | `--pale-periwinkle` | Near-white purple tint; ultra-light backgrounds |

The scale runs: deep (loud, certain) → light (calm, trust).

```css
/* Named color scale */
--color-profit:    #281350;  /* Deep anchor */
--color-pilot:     #5931DC;  /* Primary CTA */
--color-brilliant: #825BEB;  /* Medium accent */
--color-highlight: #DECEFF;  /* Product highlight / change indicator */
--color-margin:    #F6F3FF;  /* Ultra-light background */
```

### Secondary Spread (Accent Colors)

Each accent color represents a pillar or promise. All selected because they pair with purple. Subdued tones are standard; use the "+" variants sparingly for accents only.

| Name | Hex | Tone | Usage |
|------|-----|------|-------|
| **ACCESS** | `#FCF3D6` | Warm cream/yellow | — |
| **CLARITY** | `#FBEDFF` | Light lavender | — |
| **TRUST** | `#E7F9FF` | Light sky blue | — |
| **ACCESS+** | `#FFD967` | Bright gold/amber | Accent only, use sparingly |
| **CLARITY+** | `#F891FF` | Bright pink/magenta | Accent only, use sparingly |
| **TRUST+** | `#8EECFF` | Bright cyan | Accent only, use sparingly |

```css
/* Secondary spread — subdued */
--color-access:   #FCF3D6;
--color-clarity:  #FBEDFF;
--color-trust:    #E7F9FF;

/* Secondary spread — vivid (accent use only) */
--color-access-plus:  #FFD967;
--color-clarity-plus: #F891FF;
--color-trust-plus:   #8EECFF;
```

---

## 24. Typography Rules (Brand Guidelines)

### Font Roles

| Font | Conveys | When to Use | Limits |
|------|---------|-------------|--------|
| **Euclid Circular B** | Default — geometric, warm, friendly, unfussy. When bolded, commanding. Otherwise, invites conversation. Works across all audiences and financial maturity levels. | H2, subtitles, body copy, everything by default | No restrictions |
| **Space Mono** | "Tech" — precision, signals software | Labels, buttons, eyebrows, pricing tabs. | Use sparingly. When overused it becomes harsh and alienating, especially on charts. Never use for long body text. |
| **La Belle Aurore** | "People" — introduces imperfection, warmth, the Pilot human touch | Short accent phrases only | **Never more than 4 words at a time.** Beware overuse — do not use as a crutch. |

### Typography Alignment Rules

- **Always left-align text.** Text can also be right-aligned if circumstances require.
- **Text must never be centered.** No exceptions.

### Eyebrow / Label Style

Used to introduce sections. Set in Space Mono, uppercase, with tracked-out letter-spacing.

```css
.eyebrow {
  font-family: 'Space Mono', monospace;
  font-size: 12px;
  font-weight: 400;
  text-transform: uppercase;
  letter-spacing: 1.2px;
}
```

---

## 25. Gradients

Gradients suggest **transformation** — moving from one state to another. Because the Pilot brand is rigidly accurate, gradients add back the missing human nature. They invite sunlight, depth, perspective, and hint at a world outside the spreadsheet.

### Gradient Types

| Type | Description | CSS Direction |
|------|-------------|---------------|
| **Diagonal** | Linear with same tonal range, diagonal direction | `135deg` or `45deg` |
| **Vertical** | Linear with same tonal range, fully vertical | `180deg` or `0deg` |
| **Multi-directional (Ambient)** | Blurred orbs / radial gradients layered together | `radial-gradient` with blur |

### Diagonal Gradient Examples

```css
/* Deep purple diagonal */
background: linear-gradient(135deg, #281350, #5931DC);

/* Light blue/cyan diagonal */
background: linear-gradient(135deg, #E7F9FF, #8EECFF);

/* Warm gold diagonal */
background: linear-gradient(135deg, #FCF3D6, #FFD967);
```

### Vertical Gradient Examples

```css
/* Pink/lavender vertical */
background: linear-gradient(180deg, #F891FF, #FBEDFF);

/* Purple highlight vertical */
background: linear-gradient(180deg, #5931DC, #DECEFF);
```

### Multi-directional (Ambient / Blurred Orb) Examples

```css
/* Purple to gold ambient */
background: radial-gradient(ellipse at 20% 80%, #5931DC 0%, transparent 60%),
            radial-gradient(ellipse at 80% 20%, #FFD967 0%, transparent 60%);
filter: blur(0); /* applied to inner orb element */

/* Pink to cyan ambient */
background: radial-gradient(ellipse at 30% 70%, #F891FF 0%, transparent 60%),
            radial-gradient(ellipse at 70% 30%, #8EECFF 0%, transparent 60%);
```

**Rule:** Use gradients within the same tonal family. A purple gradient should move through the purple scale. Don't mix warm and cool families (e.g., orange + purple) unless you are intentionally creating an ambient/orb effect.

---

## 26. Shapes

Two core shapes define the Pilot brand:

### Lines

- Used to pin sections together or frame headers in infographics
- Lines can intersect or simply touch
- **Rule:** If you can delete a line and the design works without it, delete it

```css
/* Typical section divider line */
border-top: 1px solid #e0e0e0;

/* Colored accent line (e.g., eyebrow left-border) */
border-left: 2px solid #5931DC;
```

### Circles

- The Pilot "rising sun" — anchors subjects and adds warmth
- Can be used in every brand color
- Can be enriched using blurred gradients (ambient orb effect)
- **Always a mathematically perfect circle. No ovals.**
- Use `border-radius: 50%` with equal `width` and `height`, or `aspect-ratio: 1`

```css
.brand-circle {
  border-radius: 50%;
  aspect-ratio: 1;
  /* width and height must always be equal */
}

/* Example: purple brand circle */
.brand-circle--purple {
  background-color: #5931DC;
}

/* Example: blurred ambient orb */
.brand-orb {
  border-radius: 50%;
  aspect-ratio: 1;
  filter: blur(40px);
  opacity: 0.4;
}
```

**Color exception for circles:** Do not use `PROFIT` (`#281350`) as a circle fill. It is too dark and reads as a void rather than an anchor.

---

## 27. Drop Shadows

Drop shadows are used **only for complex graphics** that incorporate name tags, layered product snapshots, or icons. Subtle drop shadows add depth and dimension, making it easier to understand layered compositions.

### Rules

- **Only ever use purples for drop shadows.** No black, no gray, no neutral shadows.
- **Blur:** 50–100px
- **Opacity:** 10%–20%

### CSS Examples

```css
/* Minimum (lightest) drop shadow */
filter: drop-shadow(0px 20px 50px rgba(89, 49, 220, 0.10));

/* Standard drop shadow */
filter: drop-shadow(0px 30px 70px rgba(89, 49, 220, 0.15));

/* Maximum (heaviest) drop shadow */
filter: drop-shadow(0px 40px 100px rgba(89, 49, 220, 0.20));

/* CSS box-shadow equivalent (for DOM elements) */
box-shadow: 0 30px 70px rgba(89, 49, 220, 0.15);

/* Using brand purple variable */
box-shadow: 0 30px 100px rgba(93, 46, 229, 0.12); /* #5f2ee5 at ~12% */
```

**When to use:** Product screenshots floating over backgrounds, name tag cards layered over photos, icon clusters with depth. Do not add drop shadows to simple text, standalone icons, or flat layout elements.

---

## 28. Icons

### Icon Philosophy

Every Pilot icon is composed of two elements:
1. **Precise, angular lines** at exactly 45° or 90° angles — representing technology and accuracy
2. **A soft, human circle** — representing people and warmth

This combination expresses Pilot's core identity: *precision, powered by people.*

### Icon Style Specifications

| Property | Value |
|----------|-------|
| Stroke weight | 1.5–2px, consistent |
| Line angles | 45° or 90° only |
| Circle element | Present in most icons; always perfect circle |
| Color | Dark navy (`#281350`) strokes + purple circle accent (`#825BEB` or `#DECEFF`) |
| Background fill | None (outline/stroke style) or very light fill |
| Corner treatment | Sharp corners on angular elements; soft on circular |

### Do / Don't

**Do:**
- Use angular 45°/90° strokes for the "tech" elements (arrows, charts, grid lines)
- Add a soft circle element (even partially visible) to introduce the human element
- Keep stroke weights consistent across an icon set

**Don't:**
- Use curves or organic shapes for the mechanical/angular parts
- Use diagonals at arbitrary angles (only 45° or 90°)
- Mix heavy and light strokes in the same icon

### Future Icon Work

Two projects are outstanding:
- Larger illustrations (hero-scale, editorial)
- Smaller product icons (UI-scale, functional)

---

## 29. Photography

### Core Rules

1. **Real people in real situations** — we prefer an okay *real* photo over an eye-grabbing but highly treated fake one
2. **Break people out of their box** — avoid rectangular crops; use curves, circles, or cutouts

### Photography Character

We want the team's calm, confident honesty to shine through. The tone is warm, approachable, and direct — not aspirational or polished to the point of feeling fake.

### What We Look For

- People in motion or mid-thought (not posed)
- Customers should see themselves in the subject
- Any paperwork/forms should be authentic (e.g., really show Form 1040)
- Diversity of people
- Diversity of products/locations
- When in doubt: ask "which photo seems more true?"

### Avoid

- Fake smiles and improbable emotions
- Fakery like exaggerated piles of papers
- Fake monochromatic background photos
- Circular- or square-cropped headshots
- Opaque overlays / layered backgrounds

### Photo Spectrum: SMB Warm → Startup Cool

Photos also follow the people/tech spectrum. Small business owner contexts lean warm (natural light, lived-in environments). Startup/tech contexts lean cool (clean, modern workspaces).

```
SMB WARM  •————————————————————————————————•  STARTUP COOL
(warm tones, natural settings,         (clean, modern, neutral,
small biz owners, craftspeople)         startup offices, laptops)
```

### Breaking People Out of Boxes

Avoid rectangular photo boxes. Instead:
- Use **curves or circles** to frame subjects — our "rising sun" circle shape
- Enrich with **subtle monotone gradients** or **gradient halos** behind the subject
- Use **cutouts** (remove background) and place subjects into brand layouts

### Headshots

Headshots of team members and customers are an exception — **we want eye contact.** Headshots should always look friendly and approachable. Make them look good, even if you need to use AI to complete a missing shoulder.

| Property | Rule |
|----------|------|
| Shoulders | Visible |
| Expression | Friendly |
| Lighting | Warm |
| Avoid | Grayscale, photo filters |

### Black & White Photography

We only use grayscale photography in **collage-style layouts**, which we only create out of necessity. Otherwise we can't show these people, items, or situations, and it makes stock photos seem passable.

- **No people looking at the camera** in B&W collages
- Isolate subjects and place them into brand layouts
- Use when the color version isn't available or creates visual conflict

---

## 30. Backgrounds (Decorative Patterns)

Our backgrounds are **purposeful** — they foreshadow what customers will see in the product and working with us. We keep it simple and friendly, with rounded corners applied to data elements.

### Four Background Pattern Types

| Type | Description | CSS Approach |
|------|-------------|-------------|
| **Ledger** | Grid lines suggesting a spreadsheet — horizontal and vertical rules creating cells | `repeating-linear-gradient` or SVG grid |
| **Bar Chart** | Simplified bar chart columns (filled, for visual balance; fill not required) | SVG or CSS clip-path columns |
| **Highlighted Cells** | Scattered rectangular highlight marks at different sizes, suggesting active spreadsheet cells | Absolute-positioned `div` elements with low-opacity purple fill |
| **Dot Matrix** | Regular grid of small dots, suggesting data density and precision | CSS `radial-gradient` or `background-image: radial-gradient` |

### CSS Implementation

```css
/* Ledger background */
.bg-ledger {
  background-image:
    linear-gradient(to right, rgba(93, 46, 229, 0.08) 1px, transparent 1px),
    linear-gradient(to bottom, rgba(93, 46, 229, 0.08) 1px, transparent 1px);
  background-size: 80px 40px;
}

/* Dot matrix background */
.bg-dot-matrix {
  background-image: radial-gradient(circle, rgba(93, 46, 229, 0.15) 1.5px, transparent 1.5px);
  background-size: 16px 16px;
}

/* Highlighted cells (requires child elements) */
.bg-highlighted-cells {
  position: relative;
  overflow: hidden;
}
.bg-highlighted-cells::before,
.bg-highlighted-cells::after {
  content: '';
  position: absolute;
  background-color: rgba(93, 46, 229, 0.10);
  border-radius: 3px;
  /* Varied widths and positions to mimic active cells */
}
```

**Key detail:** Round the corners on bar chart bars and highlighted cell rectangles. This mirrors how the Pilot product displays data — keeping the brand consistent between marketing and product.

---

## 31. Corners & Border Radius (Brand Rules)

Traditional finance relies on grids and rigid spreadsheets — many of our clients dislike that. We deliberately round corners to varying degrees to make the brand feel more approachable.

### Corner Rules by Element Type

| Element | Radius | Notes |
|---------|--------|-------|
| **CTA Buttons (pills)** | `999px` or `100%` | Always full pill. Can add a light gradient stroke/glow for emphasis. |
| **Name cards, data boxes, info boxes** | `30px`–`40px` | "Subtle roundness." Use Figma's Scale function to maintain accurate rounding when resizing. |
| **Chat bubbles** | iPhone-style | Mimic the iPhone's native message bubble shape — they are their own design language. |
| **Cards (standard)** | `0.5rem` (8px) | Light rounding for data cards |
| **Cards (featured)** | `1rem` (16px) | More prominent rounding |
| **Form container** | `3.5rem` (56px) | Hero email capture form |
| **Pricing tabs** | `60px` | Tab switcher pill container |
| **Small UI elements** | `4px` | Minimal rounding — checkboxes, dropdown items |

### CSS Examples

```css
/* CTA pill button */
.btn-cta {
  border-radius: 999px;
}

/* Optional emphasis glow on CTA */
.btn-cta--glow {
  border-radius: 999px;
  box-shadow: 0 0 0 3px rgba(93, 46, 229, 0.15);
  /* Optional gradient stroke: */
  border: 1px solid;
  border-image: linear-gradient(135deg, #c8b6fc, #5931dc) 1;
}

/* Name / data box */
.box-name {
  border-radius: 32px; /* middle of 30–40px range */
}

/* Standard card */
.card {
  border-radius: 8px;
}

/* Featured / hero card */
.card-featured {
  border-radius: 16px;
}
```

---

## 32. Figma-Specific Notes

- When resizing rounded-corner elements (name cards, data boxes), use Figma's **Scale function** (not resize handles) to maintain accurate corner rounding proportions.
- Chat bubbles should use **auto-layout + corner smoothing** to match iOS message bubble appearance.
- Circles must always maintain equal W and H — **lock aspect ratio** before scaling.
- Drop shadow effects in Figma: use **Drop Shadow** effect, color from purple family only, blur 50–100, opacity 10–20%.
- Brand circles enriched with blurred gradients: use **blur effect** on a colored circle layer placed behind the main circle.

---

## 33. Complete CSS Variable Reference

```css
:root {
  /* ─── Official Named Colors ─── */
  --color-profit:        #281350;  /* PROFIT — darkest purple */
  --color-pilot:         #5931DC;  /* PILOT — primary brand purple */
  --color-brilliant:     #825BEB;  /* BRILLIANT — medium purple */
  --color-highlight:     #DECEFF;  /* HIGHLIGHT — product change indicator */
  --color-margin:        #F6F3FF;  /* MARGIN — near-white purple tint */

  --color-access:        #FCF3D6;  /* ACCESS — warm cream */
  --color-clarity:       #FBEDFF;  /* CLARITY — light lavender */
  --color-trust:         #E7F9FF;  /* TRUST — light sky blue */
  --color-access-plus:   #FFD967;  /* ACCESS+ — bright gold (accent only) */
  --color-clarity-plus:  #F891FF;  /* CLARITY+ — bright pink (accent only) */
  --color-trust-plus:    #8EECFF;  /* TRUST+ — bright cyan (accent only) */

  /* ─── Webflow/CSS Live Site Variables ─── */
  --pilot-black:               #3f3c3d;   /* Body text */
  --pilot-dark-purple:         #281350;   /* = PROFIT */
  --white:                     #ffffff;

  --purple--1-primary-ee5:     #5f2ee5;   /* Primary CTA purple (≈ PILOT) */
  --purple--2-beb:             #825beb;   /* = BRILLIANT */
  --purple--3-30-6fc:          #c8b6fc;   /* Light purple nav text */
  --purple--x-d89:             #3c2d89;   /* Deep purple accent */
  --purple--x-c70:             #473c70;   /* Muted dark purple */
  --purple--3-cfd:             #f0ecfd;   /* Very light purple tint */

  --light--light-5fa:          #f3f5fa;   /* Primary section background */
  --light--purple-f2edff:      #f2edff;
  --light--f8f8f8:             #f8f8f8;
  --light--blue-gray-afc:      #f9fafc;
  --light--light-ef5:          #edeef5;
  --light--light-purple-afd:   #e3dafd;
  --gray:                      #f3f5fa;
  --gray-999:                  #999;
  --gray-light:                #e0e0e0;
  --dark-gray-363:             #656363;
  --pale-periwinkle:           #f6f3ff;   /* = MARGIN */
  --transparent:               #fff0;

  --bright-blue:               #4f9bf3;
  --cta-green:                 #47bfa4;
  --error-red:                 #ce1836;
  --supernova:                 #ffcc00;
  --light-yellow:              #fee17f;
  --pilot-pink:                #f891ff;   /* = CLARITY+ */
  --pilot-pink-10:             #f891ff1a;
  --pilot-cyan:                #e7f9ff;   /* = TRUST */
  --pale-lavender:             #fef4ff;
  --buttery-cream:             #fcf3d6;   /* = ACCESS */
  --pastel-violet:             #fbedff;   /* = CLARITY */
  --olive-green:               #6e9605;
}
```
