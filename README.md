# 🌲 ArborVeil — Forest Management Landing Page

A photorealistic 3D forest management landing page built with Three.js, GSAP, and vanilla HTML/CSS/JS. Features real-world wind physics, procedural textures, volumetric god-ray lighting, and a live ecosystem data HUD — all in a single self-contained HTML file.

---

## 🚀 Quick Start

No build tools. No dependencies to install. Just open the file.

```bash
# Option 1 — Open directly in browser
open forest-management.html

# Option 2 — Serve locally (recommended for best performance)
npx serve .
# or
python -m http.server 8080
```

Then visit `http://localhost:8080/forest-management.html`

---

## ✨ Features

### 🌳 Realistic 3D Forest
- **Procedural tree generation** — every tree is unique with randomised height, trunk taper, branch angle, and foliage density
- **Two species types** — conifers (stacked cone layers) and deciduous (organic sphere cluster canopy)
- **Recursive branch system** — trunk → primary branches → secondary branches with tapering thickness
- **Buttress root flares** — large trees grow 5–8 root flanges at the base for realism
- **Vertex-level trunk deformation** — bark swell, lean, and roughness baked at geometry level
- **90+ trees rendered** in three depth rings (foreground, mid, background)

### 🎨 Procedural Textures (Zero External Assets)
| Texture | Generation Method |
|---|---|
| Bark | Vertical grain lines, horizontal cracks, moss patches on canvas |
| Leaf | HSL-shifted per tree with vein patterns drawn procedurally |
| Ground | Soil particles, scattered leaf litter, moss patches |
| Pollen Particle | Radial gradient soft circle |
| Globe Surface | Landmass ellipse blobs with colour variation |

### 💡 Physically Correct Lighting
- `ACESFilmic` tone mapping + `physicallyCorrectLights` renderer mode
- **4096×4096 shadow map** with PCF soft shadows and bias correction
- **Golden-hour sun** at low angle casting long warm shadows through canopy
- **12 animated SpotLight god rays** — each flickers at a different frequency simulating light shafting through moving leaves
- **Green sub-surface scatter** bounce light from the forest floor
- Cool blue sky fill light + warm atmospheric rim

### 🌬️ Real-World Wind Physics
- **Compound wind model** — 3 overlapping sine waves at different frequencies for natural-feeling gusts
- **Dynamic wind direction** — rotates slowly over time
- **Gust cycles** — wind strength pulses realistically every ~10 seconds
- **All elements respond** — trees, god rays, dappled lights, and 2,000 particles all react to wind

### 🌿 2,000-Particle Pollen System
- Two-axis turbulence noise for organic drift
- Wind-direction-aware horizontal movement
- Soft radial gradient circular texture
- Particles loop continuously (fall → reset to canopy height)

### 🎬 Cinematic Camera
- **Intro pull-down** — starts at 8m height, eases down to eye level (1.65m) over ~3 seconds using quartic easing
- **Slow orbital walk** — continuous gentle pan around the forest centre
- **Scroll-depth zoom** — scrolling pulls the camera forward into the forest
- **Breathing simulation** — subtle micro-rotation on Z-axis
- **Smooth lerp interpolation** — no snapping, always fluid

### 📊 Live Data HUD
Real-time ecosystem monitoring panel displayed over the hero:
- **Wind Speed** — updates dynamically every 2–5 seconds
- **Canopy Temperature** — static display
- **CO₂ Flux** — static display

---

## 🗂️ File Structure

```
forest-management.html      ← Entire app (single file, ~700 lines)
README.md                   ← This file
```

Everything — HTML, CSS, JavaScript, Three.js scene, GSAP animations — lives in one self-contained file. No build step, no node_modules, no bundler required.

---

## 📦 External Dependencies (CDN)

| Library | Version | Purpose |
|---|---|---|
| Three.js | r128 | 3D rendering engine |
| GSAP | 3.12.2 | Scroll animations & UI transitions |
| GSAP ScrollTrigger | 3.12.2 | Scroll-linked animation plugin |
| Google Fonts | — | DM Serif Display + Source Sans 3 |

All loaded via CDN — no local installation needed.

---

## 🏗️ Architecture

### Renderer Setup
```
WebGLRenderer
  ├── physicallyCorrectLights: true
  ├── toneMapping: ACESFilmicToneMapping (exposure: 0.75)
  ├── shadowMap: PCFSoftShadowMap (4096×4096)
  └── pixelRatio: min(devicePixelRatio, 2)
```

### Scene Graph
```
Scene
  ├── HemisphereLight          (sky/ground fill)
  ├── DirectionalLight (sun)   (shadows, golden hour)
  ├── DirectionalLight (sky)   (cool blue fill)
  ├── DirectionalLight (rim)   (atmospheric depth)
  ├── PointLight (bounce)      (green SSS simulation)
  ├── SpotLight × 12           (god rays, animated)
  ├── Terrain (PlaneGeometry)  (160×160 segments, multi-octave noise)
  ├── Undergrowth              (80 bushes + 120 ferns)
  ├── Tree × 104               (foreground/mid/background rings)
  ├── God Ray Planes × 10      (additive blended, animated opacity)
  └── Particles (Points × 2000)(pollen/spore drift)
```

### Animation Loop (per frame)
1. Compound wind model → tree rotation
2. SpotLight intensity flicker (god rays through moving leaves)
3. Particle turbulence + wind drift
4. Camera lerp (orbital + scroll zoom + breathing)
5. `renderer.render(scene, camera)`

---

## 📄 Page Sections

| Section | Description |
|---|---|
| **Hero** | Fullscreen 3D forest, data HUD, animated title + CTA |
| **About** | Stats grid with animated counters (4.2M ha, 890K tonnes CO₂, etc.) |
| **Services** | Horizontal drag-scroll cards with 3D tilt on hover |
| **Globe** | Rotating 3D Earth with forest zone markers and atmosphere glow |
| **CTA** | Email sign-up with mist animation |
| **Footer** | Brand, tagline, country/hectare summary |

---

## 🖥️ Browser Compatibility

| Browser | Support |
|---|---|
| Chrome 90+ | ✅ Full |
| Firefox 88+ | ✅ Full |
| Safari 15+ | ✅ Full |
| Edge 90+ | ✅ Full |
| Mobile Chrome | ⚠️ Reduced (some features hidden) |

> **Performance note:** The forest scene targets 60fps on modern GPUs. On low-end devices, reduce `particleCount` (line ~350) from 2000 to 800, and tree counts from 104 to 60 for better performance.

---

## ⚙️ Customisation

### Change Forest Density
```js
// In the "Plant the forest" section (~line 370)
for(let i=0;i<55;i++){  // ← Background trees (default: 55)
for(let i=0;i<35;i++){  // ← Mid-ring trees (default: 35)
for(let i=0;i<14;i++){  // ← Foreground trees (default: 14)
```

### Change Wind Intensity
```js
// In the render loop
windStrength = 0.4 + gust * 0.8;  // ← Increase multiplier for stronger wind
```

### Change Time of Day (Lighting)
```js
// Sun colour (golden hour = 0xffe8a0, midday = 0xfff8f0, overcast = 0xb0c8d0)
const sun = new THREE.DirectionalLight(0xffe8a0, 4.5);

// Sun position (low = golden hour, high = midday)
sun.position.set(22, 18, 8);  // ← Lower Y = more dramatic shadows
```

### Change Fog Density
```js
scene.fog = new THREE.FogExp2(0x0d1f10, 0.022);  // ← Higher = denser fog
```

### Change Camera Speed
```js
camAngle += 0.0015;  // ← Increase for faster orbit
```

---

## 🌍 Globe Data Points

Forest zone markers are defined as `[latitude, longitude]` pairs:

```js
[[5,-60],[-5,20],[0,110],[55,80],[-25,-50],[10,15],
 [45,130],[-10,35],[62,25],[-3,105],[20,-100],[35,60],
 [-15,170],[10,-10],[-30,25],[15,45]]
```

Add or remove entries to adjust monitored forest zones displayed on the globe.

---

## 📐 Design System

| Token | Value |
|---|---|
| Background | `#010804` |
| Bio Green | `#7eff9a` |
| Bio Light | `#c8f5b0` |
| Text | `#e2f0e6` |
| Text Dim | `#7aaa8a` |
| Display Font | DM Serif Display |
| Body Font | Source Sans 3 |
| Tone Mapping | ACESFilmic (exposure 0.75) |

---

## 📜 License

Built for ArborVeil Forest Intelligence. All procedural textures and geometry are generated at runtime — no third-party assets required.

---

*"The forest needs guardians."* 🌿
