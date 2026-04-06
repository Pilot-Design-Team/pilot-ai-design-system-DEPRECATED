# Strata / Pilot Icon System — Complete Specification

> **Use this document as the single source of truth** to recreate Pilot-style icons in any system (Figma, another codebase, design tool, etc.).

---

## Design Philosophy

Every Pilot icon communicates one idea through **exactly two visual elements**:

1. **Precision lines** — Sharp, angular, geometric strokes representing structure, accuracy, and technology.
2. **The People Dot** — A single soft, filled circle representing the human element.

> *Precision, powered by people.*

The combination of hard geometry + one soft circle is what makes every Pilot icon immediately recognizable. **Both elements must always be present.** An icon without the dot is not a Pilot icon.

---

## Technical Specifications

### SVG Canvas

| Property     | Value           | Notes                                      |
|--------------|-----------------|---------------------------------------------|
| ViewBox      | `0 0 24 24`     | All icons drawn on a 24×24 unit grid        |
| Render size  | `45px`–`50px`   | Physical display size (width/height attrs)  |
| Background   | **Transparent** | Never place a colored box behind the icon   |

### Structural Lines (Precision Element)

| Property        | Value            | Notes                                         |
|-----------------|------------------|-----------------------------------------------|
| Stroke color    | `currentColor`   | Inherits from parent — allows theming         |
| Stroke width    | `1.5`            | Exception: `IconCheck` uses `2.5` for weight  |
| Stroke linecap  | `square`         | Not `round` — keeps endpoints sharp           |
| Stroke linejoin | `miter`          | Not `round` — keeps corners sharp             |
| Fill            | `none`           | Lines are always stroked, never filled         |
| Angle constraint| 0°, 45°, or 90°  | All structural paths use only these angles    |

### The People Dot

| Property    | Value                          | Notes                                            |
|-------------|--------------------------------|--------------------------------------------------|
| Element     | `<circle>`                     | Always a circle, never a square or other shape   |
| Fill color  | `var(--icon-dot)` / `#bdb0f8`  | Soft lavender-purple — consistent across ALL icons |
| Stroke      | `none`                         | The dot has no outline                           |
| Opacity     | `1`                            | Solid, never transparent                         |
| Radius      | `3`–`5` units                  | Within the 24×24 viewBox (typically `r="4"`)     |
| Fill rule   | The dot sits ON TOP of lines   | It's a `<circle>` rendered before or after paths, overlapping structural geometry |

### Dot Placement Rules

The dot's position varies per icon to create visual balance. Follow these guidelines:

| Guideline                     | Detail                                                                 |
|-------------------------------|------------------------------------------------------------------------|
| **One dot per icon**          | Never use two dots. Never omit the dot.                                |
| **Corner-biased placement**   | Dots typically sit near a corner of the 24×24 canvas (e.g., `cx="19" cy="18"`, `cx="5" cy="5"`) |
| **Overlap structural lines**  | The dot should partially overlap or touch the geometric element — it's integrated, not floating in empty space |
| **Asymmetric**                | Don't center the dot — offset placement creates visual interest        |
| **Vary position across icons**| Distribute dots across different corners (top-left, top-right, bottom-left, bottom-right) so a set of icons doesn't look repetitive |

Common positions used in the current set:
- Top-left: `cx="5" cy="5"` or `cx="5" cy="6"`
- Top-right: `cx="19" cy="5"` 
- Bottom-left: `cx="4" cy="19"` or `cx="5" cy="19"`
- Bottom-right: `cx="19" cy="18"` or `cx="18" cy="18"`

---

## Sizing Guide

| Context                 | Render Size | Example                          |
|-------------------------|-------------|-----------------------------------|
| Primary feature cards   | `50px`      | Homepage hero features            |
| Secondary grid icons    | `45px`      | Product/Security page grids       |
| Supporting / inline     | `20`–`30px` | List bullets, small callouts      |
| Checkmarks              | `16`–`20px` | Inline list check icons           |

---

## Critical Rules

1. **NO background.** Icons are always transparent. Never wrap in a colored circle, square, or badge.
2. **Icons are standalone.** They must be clear and legible without any background treatment.
3. **One dot, always.** Every icon gets exactly one purple dot. No exceptions.
4. **Square linecap + miter join.** This is what gives icons their angular, precise look. Using `round` will break the style.
5. **`currentColor` for strokes.** Never hard-code a stroke color. This allows the icon to inherit color from its parent for light/dark theming.
6. **The dot color is fixed.** Even when `currentColor` changes (e.g., white text on dark bg), the dot is always `#bdb0f8`.

---

## CSS Variable

Define this in your global stylesheet:

```css
--icon-dot: #bdb0f8;
```

---

## SVG Template

Copy this as a starting point for any new icon:

```svg
<svg width="45" height="45" viewBox="0 0 24 24" fill="none"
     stroke="currentColor" stroke-width="1.5"
     stroke-linecap="square" stroke-linejoin="miter">
  <!-- People Dot — pick a corner position -->
  <circle cx="19" cy="18" r="4" fill="var(--icon-dot)" stroke="none" />
  <!-- Structural geometry — use only 0°/45°/90° lines -->
  <path d="..." />
</svg>
```

---

## React Component Template

```tsx
interface PilotIconProps {
  size?: number;
  className?: string;
  color?: string;      // overrides currentColor for structural lines only
}

export function IconExample({ size = 24, className, color }: PilotIconProps) {
  return (
    <svg width={size} height={size} viewBox="0 0 24 24" fill="none"
      className={className}
      stroke={color || "currentColor"} strokeWidth="1.5"
      strokeLinecap="square" strokeLinejoin="miter">
      <circle cx="19" cy="18" r="4" fill="var(--icon-dot)" stroke="none" />
      <path d="..." />
    </svg>
  );
}
```

---

## Icon Library Reference

The following icons are currently implemented in `PilotIcons.tsx`:

| Export Name       | Concept              | Dot Position   |
|-------------------|----------------------|----------------|
| `IconPeople`      | People / Hiring      | bottom-right   |
| `IconFinance`     | Dollar / Finance     | top-left       |
| `IconChecklist`   | Checklist / Verify   | top-right      |
| `IconAutomation`  | Lightning / Speed    | bottom-right   |
| `IconReview`      | Eye / Review         | bottom-left    |
| `IconGrowth`      | Growth / Scaling     | bottom-left    |
| `IconSecurity`    | Shield / Security    | bottom-right   |
| `IconGlobe`       | Globe / Residency    | top-left       |
| `IconLock`        | Lock / Encryption    | top-right      |
| `IconAccess`      | Access Control       | bottom-left    |
| `IconAlert`       | Alert / Breach       | bottom-right   |
| `IconDelete`      | Delete / Removal     | top-left       |
| `IconDocument`    | Document / File      | bottom-right   |
| `IconContainer`   | Container / Isolation| top-right      |
| `IconLogs`        | Logs / Records       | bottom-left    |
| `IconPartner`     | Partner / Handshake  | bottom-right   |
| `IconNoMarketing` | No Marketing         | top-left       |
| `IconCheck`       | Checkmark            | top-right      |
| `IconRobot`       | Robot / AI           | top-right      |
| `IconSync`        | Sync / Integration   | bottom-left    |

---

## Checklist: Creating a New Pilot Icon

- [ ] Start with the `0 0 24 24` viewBox
- [ ] Set `stroke="currentColor"`, `stroke-width="1.5"`, `stroke-linecap="square"`, `stroke-linejoin="miter"`, `fill="none"`
- [ ] Draw structural geometry using **only 0°, 45°, or 90° angles**
- [ ] Add exactly **one** `<circle>` with `fill="var(--icon-dot)"` and `stroke="none"`
- [ ] Place the dot at a corner position that overlaps or touches the geometry
- [ ] Vary the dot position relative to other icons in the same set
- [ ] Render at `45px`–`50px` for feature contexts
- [ ] **No background** — transparent only
- [ ] Test on both light and dark surfaces (stroke should inherit `currentColor`)
