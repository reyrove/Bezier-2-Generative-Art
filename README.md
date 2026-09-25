# Bezier 2

**A seed-based generative system for slow rotating bezier curves.**

A catalogue of computational textile compositions for fashion, textile and surface design — algorithmically drawn, seed-documented, and ready for production.

---

## Overview

Bezier 2 is a generative design system rather than a single artwork. Each composition is built from a single closed bezier path whose control points drift inward and outward along radial lines, while the whole form rotates imperceptibly and its colour gradient sweeps continuously from one end of the palette to the other.

The system is designed for:

- **Fashion houses** adapting motion-driven ornament for apparel and accessories
- **Textile studios** developing repeat patterns and yardage
- **Surface designers** working across print, wallpaper, and interior applications

Every composition can be licensed, adapted, or commissioned to a brief.

---

## Concept

A curve, when it is *set in motion*, becomes a rhythm — slow, continuous, quietly yours.

The closed curve has always carried motion: the turning of a wheel, the breathing of a border, the slow ornament of a garden path. Bezier 2 translates that motion into code. Each composition begins with a palette and a count, and unfolds through a single closed bezier path whose control points drift along radial lines — the whole form rotating imperceptibly, its colour gradient sweeping continuously.

The palette, the number of control points, the drift range, and the rotation speed are all derived from a single numeric seed.

Unlike the other volumes in the series, **Bezier 2 is the only composition in the catalogue that is animated on the live plate.** The motion is part of its identity: it is the "slow" volume. Where Girih and Arachne are static prints, Bezier 2 is a rhythm — the plate breathes, the archive and surfaces stand still.

---

## Features

- **Seed-based generation** — every composition is defined by a numeric seed and can be regenerated exactly
- **Deterministic output** — the same seed always produces the same composition at any given frame
- **Animated plate** — the live Plate 001 rotates and drifts continuously
- **Static catalogue** — the framed plate, surfaces, and archive thumbnails are all frozen single frames, suitable for print
- **Gradient curves** — colour interpolates continuously across the length of the path
- **Adaptive surfaces** — one seed applied across print, scarf, textile, and wall formats
- **Archive** — eight curated seeds available for immediate loading
- **Download** — export the current frame as a high-resolution PNG
- **Keyboard shortcuts** — `R` for new seed, `S` to save

---

## Project Structure

```
.
├── index.html          # Main catalogue page
├── images/
│   ├── fav.svg         # Favicon
│   ├── tote.png        # Mockup: tote bag
│   ├── tee.png         # Mockup: t-shirt
│   └── cushion.png     # Mockup: cushion
└── README.md
```

---

## How It Works

### The Seed

A numeric seed (a large integer) initializes a deterministic pseudo-random generator. From this seed, the system derives:

- Background colour (from a palette of 28 deep tones)
- Two foreground colours for the gradient (from a palette of 28 tones)
- Number of control points (typically 3–30)
- Position of each control point
- Drift range and step for each point (how far it moves inward/outward)
- Direction of drift (a binary coefficient per point)
- Line width
- Rotation speed

Because the generator is deterministic, the same seed always produces the same composition — on any device, at any time.

### The Curves

Each composition draws a single closed bezier path through a set of control points arranged roughly around a circle.

- **Control points** are placed at irregular angles and radii, so the path is not a perfect circle.
- **Drift** moves each control point inward or outward along its radial line, bouncing when it reaches its assigned range. This is what makes the curve "breathe".
- **Rotation** turns the whole form slowly around the centre. The default speed is roughly one full revolution every 1,600 to 16,000 frames — a hand's width over half a minute.
- **Gradient** interpolates continuously between two foreground colours along the length of the path: the first colour runs from the start to the midpoint, and the second colour runs from the midpoint back to the start.

### The Surfaces

The same seed is rendered across four surface formats. These are **static, frozen at frame zero** — they represent the print-ready composition, not the animation.

| Surface  | Aspect | Material          |
|----------|--------|-------------------|
| Print    | 1 : 1  | Cotton rag        |
| Scarf    | 3 : 1  | Twill silk        |
| Textile  | 4 : 3  | Fabric yardage    |
| Wall     | 2 : 3  | Wallpaper         |

Each surface uses the same underlying seed and structural logic — only the repeat, orientation, and scale change.

### Animation

Bezier 2 is the only volume in the series where the live plate is animated. The animation behaves like this:

- **Plate 001** — animated continuously via `requestAnimationFrame`. Rotation advances by the seed's own rotation speed each frame, and the control points drift one step per frame.
- **Framed plate, surfaces, archive thumbnails, cover** — rendered as single, static frames at angle zero. They do not animate.
- **Download** — pauses the plate animation, captures the current frame as a PNG, then resumes.
- **Tab visibility** — animation pauses when the tab is hidden and restarts cleanly when you return.
- **Reduced motion** — if the user has `prefers-reduced-motion: reduce`, the plate renders a single frame and does not animate.

The reason only the plate animates: the catalogue exists to present print-ready compositions. Surfaces and archive thumbnails must be comparable at a glance, and eight simultaneously animating thumbnails would be heavy and visually confusing. The live plate, however, is where the character of Bezier 2 — motion — is expressed.

---

## Usage

### In the browser

1. Open `index.html` in any modern browser.
2. The Plate 001 composition animates on its own.
3. Click **New Seed** to generate a new composition.
4. Click **Download** to save the current frame as a PNG.
5. Scroll to the **Archive** section and click any plate to load it into Plate 001.

### Keyboard shortcuts

| Key | Action          |
|-----|-----------------|
| `R` | New seed        |
| `S` | Save as PNG     |

### Reproducing a composition

Each composition is identified by an 8-digit seed label displayed in the metadata panel. To reproduce a specific composition statically, note the seed and regenerate it programmatically:

```js
const rng = new RandomGenerator(seed);
setup();
renderComposition(canvas, { features, angle: 0, advance: false });
```

For an animated reproduction, use the same pattern with a `requestAnimationFrame` loop, incrementing `angle` by `features.rotSpeed` each frame and calling `renderComposition` with `advance: true`.

---

## Technical Notes

- **No build step.** The system is a single HTML file with inline CSS and JavaScript.
- **No dependencies.** All drawing is done with the native Canvas 2D API.
- **Deterministic.** The `RandomGenerator` class uses a xorshift-based PRNG seeded by an integer, so identical seeds produce identical outputs.
- **Animation isolated to the plate.** Only the live Plate 001 uses `requestAnimationFrame`. All other canvases render a single frame and stop.
- **Feature isolation.** Cover, framed plate, surfaces, and archive thumbnails each derive their own feature set from their own seed, without disturbing the main plate's state.
- **Responsive.** The layout adapts from large desktop down to very small mobile devices (tested at 360px viewport width).
- **Accessible.** Supports `prefers-reduced-motion`. Pinch-zoom is enabled.

### Browser support

Tested in current versions of:

- Chrome / Edge
- Firefox
- Safari (desktop and iOS)

---

## Licensing

All Bezier 2 compositions are **seed-documented** and available for licensing across textile, surface, and print applications.

- **Standard licenses** cover single-product production runs.
- **Commercial use, custom editions, or exclusive rights** are available on request.

Each license is issued against a specific seed ID. Regeneration of the same seed produces the identical composition — ensuring reproducibility between artist, studio, and manufacturer.

For licensing enquiries: [reyhanehdaneshdoost@gmail.com](mailto:reyhanehdaneshdoost@gmail.com)

---

## Commission

Bezier 2 is a generative design system, not a fixed artwork. It can be adapted for specific briefs:

| Service     | Description                                                       |
|-------------|-------------------------------------------------------------------|
| Licensing   | Existing seeds from the archive, licensed for production use      |
| Commission  | New compositions designed to your palette, repeat, and product    |
| Systems     | A private generative tool built for your studio's ongoing use     |

To begin a conversation: [reyhanehdaneshdoost@gmail.com](mailto:reyhanehdaneshdoost@gmail.com)

---

## Series

Bezier 2 is part of a computational textile series. Each volume approaches ornament from a different structural angle:

| Volume             | Structure          | Motion              |
|--------------------|--------------------|---------------------|
| Girih 1            | Islamic geometric  | Static              |
| Arachne            | Rotating rings     | Static              |
| Baroque Me Baby    | Baroque frames     | Static              |
| Bezier 1           | Concentric curves  | Static              |
| **Bezier 2**       | Single closed curve| **Animated (plate)**|

The series is designed as a coherent whole — same page structure, same seed logic, same licensing and commission terms — so that each volume can be presented individually or as part of a larger body of work.

---

## Credits

- **Design & Generative System** — Reyhaneh Daneshdoost
- **Typefaces** — Cormorant Garamond · DM Mono
- **Platform** — Reyrove Studio
- **Edition** — Bezier 2, Autumn 2026

### On AI tools

Where technical obstacles were encountered, AI tools were used for debugging and code optimization. Every structural, aesthetic, and conceptual decision remained the artist's own.

---

## Links

- Website — [reyrove.github.io](https://reyrove.github.io/)
- Instagram — [@rey._.rove](https://www.instagram.com/rey._.rove/)
- LinkedIn — [Reyhaneh Daneshdoost](https://www.linkedin.com/in/reyhaneh-daneshdoost-730481160/)
- X — [@reyrove](https://x.com/reyrove)

---

© Bezier 2 · All compositions reproducible by seed · Computational Textile Design