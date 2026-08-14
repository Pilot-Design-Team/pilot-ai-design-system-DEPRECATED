# Fonts

Two of Pilot's three brand faces ship in this repo. The third does not.

| Font | In this repo? | Why |
| --- | --- | --- |
| **Space Mono** | ✅ Yes | Open licensed (SIL OFL) |
| **La Belle Aurore** | ✅ Yes | Open licensed (SIL OFL) |
| **Euclid Circular B** | ❌ No | Licensed to Pilot. Redistributing it publicly would breach that license |

## Getting Euclid Circular B (Pilot internal)

Euclid is the body font for everything. Without it, the visualizer and any page
you build fall back to the system sans — usable, but not on brand.

Ask the design team for the brand font package, or pull it from the Pilot brand
Drive alongside the [media kit](https://drive.google.com/drive/folders/1h5BirEATWxpMydrbScK5M-YV8zKhRJmP).
Drop these eight files into this directory:

```
EuclidCircularB-Regular-WebS.woff
EuclidCircularB-Regular-WebS.woff2
EuclidCircularB-Regular-WebXL.woff
EuclidCircularB-Regular-WebXL.woff2
EuclidCircularB-Semibold-WebS.woff
EuclidCircularB-Semibold-WebS.woff2
EuclidCircularB-Semibold-WebXL.woff
EuclidCircularB-Semibold-WebXL.woff2
```

That is the whole setup. `.gitignore` already excludes `EuclidCircularB-*`, so
you cannot commit them by accident. Open `marketing/index.html` and the
visualizer will render in Euclid.

## Two rules

**Never commit Euclid to this repo.** It is public. Anything pushed here stays
in Git history permanently, even if a later commit deletes it.

**Never load Euclid from a third-party font CDN.** Sites like `cdnfonts.com`
host commercial faces without the foundry's permission. Serving Pilot's brand
font through one puts the licence at risk and makes the brand depend on
somebody else's uptime. Use the licensed files in this directory, which is what
`index.html` does.

## How it is wired

`marketing/index.html` declares the face from local files, so it renders when
they are present and degrades cleanly when they are not:

```css
@font-face {
  font-family: 'Euclid Circular B';
  src: url('fonts/EuclidCircularB-Regular-WebS.woff2') format('woff2'),
       url('fonts/EuclidCircularB-Regular-WebS.woff') format('woff');
  font-weight: 400;
  font-display: swap;
}

@font-face {
  font-family: 'Euclid Circular B';
  src: url('fonts/EuclidCircularB-Semibold-WebS.woff2') format('woff2'),
       url('fonts/EuclidCircularB-Semibold-WebS.woff') format('woff');
  font-weight: 600 700;
  font-display: swap;
}
```

Copy that block into any project you build, keeping the same fallback chain:

```css
font-family: 'Euclid Circular B', system-ui, -apple-system, sans-serif;
```
