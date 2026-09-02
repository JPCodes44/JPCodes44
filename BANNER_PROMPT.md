# Prompt: JP Mak Animated GitHub Profile Banner

Copy everything below into Claude and run it from the root of this repo.

---

## The Prompt

Build me an animated GitHub profile banner as a single self-contained SVG file, replacing the existing `animated_banner.svg` in this repo (keep the same filename so my README reference doesn't break).

### 1. Layout & composition

- Banner dimensions: 1280 × 400 (wide GitHub README banner format), responsive via `viewBox`.
- Use my photo at `assets/banner-photo.png` as the visual centerpiece — it's me in a Yoshi hat punching a Mario question block against a red-tiled wall. Place it on the **right third** of the banner, embedded as a base64 data URI inside the SVG (GitHub's camo proxy blocks external image references, so everything must be inlined).
- Give the photo a subtle treatment so it blends with the design: a soft rounded-corner mask or a pixel-dissolve edge on its left side, so it fades into the banner background instead of ending in a hard rectangle.
- Pull the banner's background palette from the photo: deep reds / crimson diamond tones from the tiled wall, with the yellow of the question block as an accent color. Dark enough that text pops.

### 2. Typography — "JP Mak"

- The name **"JP Mak"** is the focal point, placed on the left two-thirds of the banner, large.
- Font: **VG5000** by Velvetyne (https://velvetyne.fr/fonts/vg5000/ — free/libre, SIL OFL licensed). Download the font, then either:
  - **(a)** convert the "JP Mak" text to SVG path outlines (most reliable — renders identically everywhere), or
  - **(b)** subset the font to just the needed glyphs and embed it as a base64 `@font-face` inside the SVG's `<style>` block.
  Prefer (a) unless there's a reason not to.
- Animate the name's entrance: letters materialize as if being assembled — e.g., a brief per-letter pixel/glitch build-in, staggered left to right, settling into the final crisp form. Loop-friendly (either loop the whole scene or let the name settle permanently while ambient animations keep looping).

### 3. Sub-banner animation strip — AI systems × nanotechnology, pixels only

Directly **underneath "JP Mak"**, create a horizontal animated strip that fuses two ideas using **only square pixels** (no smooth curves, no gradients on the pixel elements — every element in this strip is a small `<rect>`):

- **AI systems**: a pixelated neural network — nodes as single bright pixels or 2×2 pixel clusters, connections as dotted pixel lines. Animate signal pulses: pixels lighting up and traveling along the connections node-to-node, like data flowing through a network.
- **Nanotechnology**: pixel "nanobots" — tiny pixel clusters that drift, assemble into small lattice/molecule structures (hexagons, grids), hold briefly, then disassemble and reform elsewhere. Think self-assembling matter, rendered in chunky pixels.
- Blend the two: the neural net pulses can trigger nearby nanobot assemblies, so the strip reads as one living system rather than two separate doodles.
- Color the strip with the banner accents (question-block yellow, warm reds, plus one cool contrast color like cyan for the "AI signal" pulses so they read clearly).
- Keep it subtle and ambient — it should feel alive without being distracting or seizure-inducing. Slow pulses, gentle drift, seamless loop.

### 4. Technical constraints (GitHub README compatibility)

- Single `.svg` file, fully self-contained: all images base64-inlined, all fonts either outlined to paths or base64-embedded, no external URLs of any kind.
- Animations via **SMIL (`<animate>`, `<animateTransform>`) or CSS keyframes inside a `<style>` tag** — both work when the SVG is displayed via `<img>` in a GitHub README. **No JavaScript** (GitHub strips/ignores it in `<img>` context).
- All animations must loop seamlessly and run at a reasonable performance cost (avoid animating hundreds of elements with independent complex timing; group where possible).
- Keep total file size reasonable (< ~1.5 MB if possible — compress/resize the base64 photo before embedding).
- Verify the final SVG renders correctly by opening it locally, and check the README still references it properly.

### 5. Deliverables

1. Updated `animated_banner.svg` (same path/filename).
2. If you subset or convert the VG5000 font, note the font's SIL OFL license with attribution in a comment at the top of the SVG.
3. Confirm the README banner reference still works; update it only if needed.
