<div align="center">

<img src="https://img.shields.io/badge/ArborVeil-Forest%20Management-1a6b2a?style=for-the-badge&logo=three.js&logoColor=7eff9a" alt="ArborVeil Banner"/>

# 🌲 ArborVeil — Forest Management Landing Page

### *Photorealistic 3D Forest with Live Wind Physics, God-Ray Lighting & Ecosystem HUD*

<br/>

[![Live Demo](https://img.shields.io/badge/🌐%20Live%20Demo-GitHub%20Pages-1a6b2a?style=for-the-badge)](https://manikanta-04.github.io/Forest_management/)

<br/>

[![Three.js](https://img.shields.io/badge/Three.js-r128-000000?style=flat-square&logo=three.js)](https://threejs.org)
[![GSAP](https://img.shields.io/badge/GSAP-3.12.2-88CE02?style=flat-square)](https://gsap.com)
[![Vanilla JS](https://img.shields.io/badge/Vanilla-JS-F7DF1E?style=flat-square&logo=javascript&logoColor=black)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
[![Zero Dependencies](https://img.shields.io/badge/Local%20Dependencies-Zero-brightgreen?style=flat-square)]()
[![Single File](https://img.shields.io/badge/Single%20HTML%20File-~700%20lines-blueviolet?style=flat-square)]()
[![License: MIT](https://img.shields.io/badge/License-MIT-green?style=flat-square)](LICENSE)

</div>

---

## 🚀 Live Demo

| Service | URL |
|---|---|
| 🌐 **ArborVeil Live** | [manikanta-04.github.io/Forest_management](https://manikanta-04.github.io/Forest_management/) |

> ⚡ No login. No install. Just open and experience the forest.

---

## 🎥 Demo Video

> 📽️ *(Add a Loom / YouTube demo walkthrough here)*
>
> [![Watch Demo](https://img.shields.io/badge/▶%20Watch%20Demo-YouTube-red?style=for-the-badge&logo=youtube)](https://youtube.com)

---

## 🧠 Problem Statement

Forest management organizations need immersive, data-rich digital presences — but most landing pages are static, flat, and fail to convey the living, breathing complexity of forest ecosystems. Current challenges:

- 🌲 No web experience captures the true visual scale and atmosphere of a real forest
- 📊 Ecosystem data dashboards are dry and disconnected from the environment they represent
- 🎨 3D web projects are bloated — require massive build toolchains, node_modules, and bundlers
- 🌬️ Most 3D scenes use static lighting — no wind, no life, no dynamism

**A forest management platform should feel like standing inside the forest.**

---

## 💡 Solution

**ArborVeil** is a fully self-contained, single HTML file that renders a photorealistic 3D forest with real-world wind physics, volumetric god-ray lighting, 2,000-particle pollen systems, and a live ecosystem data HUD — all via Three.js and GSAP loaded from CDN. No build step. No node_modules. Just open and explore.

> *"The forest needs guardians."* 🌿

---

## 🖼️ Screenshots

| Hero — 3D Forest Scene | God-Ray Lighting |
|---|---|
| ![Hero](screenshots/hero.png) | ![GodRay](screenshots/godray.png) |

| Ecosystem Data HUD | Globe Section |
|---|---|
| ![HUD](screenshots/hud.png) | ![Globe](screenshots/globe.png) |

| Services Cards | CTA Section |
|---|---|
| ![Services](screenshots/services.png) | ![CTA](screenshots/cta.png) |

> 📌 *(Replace with actual screenshots from your deployed page)*

---

## 🏗️ Architecture

```
┌──────────────────────────────────────────────────────────┐
│                  SINGLE FILE APP                          │
│                   index.html (~700 lines)                 │
│                                                           │
│  ┌─────────────────────────────────────────────────────┐  │
│  │                THREE.JS SCENE GRAPH                  │  │
│  │                                                      │  │
│  │  HemisphereLight + DirectionalLight (sun/sky/rim)   │  │
│  │  SpotLight × 12 (animated god rays)                 │  │
│  │  Terrain (PlaneGeometry, 160×160 segments)          │  │
│  │  Tree × 104 (3 depth rings, procedural generation)  │  │
│  │  Undergrowth (80 bushes + 120 ferns)                │  │
│  │  God Ray Planes × 10 (additive blended)             │  │
│  │  Particles (Points × 2000, pollen drift)            │  │
│  │  Globe (RotatingEarth + atmosphere + markers)       │  │
│  └─────────────────────────────────────────────────────┘  │
│                                                           │
│  ┌──────────────────────────────────────────────────┐     │
│  │               ANIMATION LOOP (60fps)              │     │
│  │  Compound wind model → tree rotation              │     │
│  │  SpotLight flicker → god ray simulation           │     │
│  │  Particle turbulence → pollen drift               │     │
│  │  Camera lerp → orbital + scroll zoom + breathing  │     │
│  └──────────────────────────────────────────────────┘     │
│                                                           │
│  CDN: Three.js r128 · GSAP 3.12.2 · Google Fonts         │
└──────────────────────────────────────────────────────────┘
```

---

## ⚙️ Tech Stack

| Layer | Technology | Purpose |
|---|---|---|
| **3D Engine** | Three.js r128 | WebGL scene, lighting, geometry |
| **Animation** | GSAP 3.12.2 | Scroll animations, UI transitions |
| **Scroll** | GSAP ScrollTrigger | Scroll-linked camera zoom |
| **Structure** | HTML5 | Single-file page markup |
| **Styling** | CSS3 | Design system, section layouts |
| **Logic** | Vanilla JavaScript ES6+ | Scene, physics, camera, HUD |
| **Fonts** | Google Fonts CDN | DM Serif Display + Source Sans 3 |
| **Hosting** | GitHub Pages | Free static hosting |

> ✅ **Zero local dependencies** — everything loaded via CDN. No npm, no build step.

---

## ✨ Features

### 🌳 Photorealistic 3D Forest (104 Trees)
- **Procedural tree generation** — every tree unique: randomized height, trunk taper, branch angle, foliage density
- **Two species** — conifers (stacked cone layers) and deciduous (sphere cluster canopy)
- **Recursive branch system** — trunk → primary → secondary branches with tapering thickness
- **Buttress root flares** — large trees grow 5–8 root flanges at base
- **Vertex-level trunk deformation** — bark swell, lean, roughness baked at geometry level
- **3 depth rings** — foreground (14), mid (35), background (55) trees

### 🎨 Procedural Textures (Zero External Assets)
| Texture | Generation Method |
|---|---|
| Bark | Vertical grain lines + horizontal cracks + moss patches on canvas |
| Leaf | HSL-shifted per tree with vein patterns drawn procedurally |
| Ground | Soil particles + scattered leaf litter + moss patches |
| Pollen | Radial gradient soft circle |
| Globe Surface | Landmass ellipse blobs with color variation |

### 💡 Physically Correct Lighting
- `ACESFilmic` tone mapping + `physicallyCorrectLights` renderer mode
- **4096×4096 shadow map** with PCF soft shadows
- **Golden-hour sun** — long warm shadows through canopy
- **12 animated SpotLight god rays** — each flickers at a different frequency
- Green sub-surface scatter bounce light from forest floor

### 🌬️ Real-World Wind Physics
- **Compound wind model** — 3 overlapping sine waves at different frequencies
- **Dynamic wind direction** — rotates slowly over time
- **Gust cycles** — wind strength pulses every ~10 seconds
- **All elements react** — trees, god rays, dappled lights, 2,000 particles

### 🌿 2,000-Particle Pollen System
- Two-axis turbulence noise for organic drift
- Wind-direction-aware horizontal movement
- Particles loop continuously (fall → reset to canopy height)

### 🎬 Cinematic Camera System
- **Intro pull-down** — starts at 8m height, eases to eye level (1.65m) over ~3s using quartic easing
- **Slow orbital walk** — continuous gentle pan around forest centre
- **Scroll-depth zoom** — scrolling pulls camera forward into the forest
- **Breathing simulation** — subtle micro-rotation on Z-axis
- **Smooth lerp** — always fluid, no snapping

### 📊 Live Ecosystem Data HUD
- **Wind Speed** — updates dynamically every 2–5 seconds
- **Canopy Temperature** — real-time display
- **CO₂ Flux** — real-time display

### 🌍 Interactive 3D Globe
- Rotating Earth with atmosphere glow effect
- 16 forest zone markers at real latitude/longitude coordinates
- Displayed in dedicated globe section of the page

---

## 📄 Page Sections

| Section | Description |
|---|---|
| **Hero** | Fullscreen 3D forest, ecosystem HUD, animated title + CTA |
| **About** | Stats grid with animated counters (4.2M ha, 890K tonnes CO₂, etc.) |
| **Services** | Horizontal drag-scroll cards with 3D tilt on hover |
| **Globe** | Rotating 3D Earth with forest zone markers + atmosphere glow |
| **CTA** | Email sign-up with mist animation |
| **Footer** | Brand, tagline, country/hectare summary |

---

## 📊 System Design

```
Three.js Render Loop (per frame ~16ms at 60fps):

1. Compound wind model computed
   → windStrength = base + gust × multiplier
   → windDirection rotates slowly over time

2. All 104 trees updated
   → rotation.z += windStrength × treeWeight

3. SpotLight × 12 flicker
   → each at unique frequency → god ray shimmer

4. 2,000 particles updated
   → turbulence noise + wind drift applied
   → fallen particles reset to canopy height

5. Camera lerp applied
   → orbital angle increments
   → scroll zoom interpolated
   → breathing micro-rotation added

6. renderer.render(scene, camera)
```

```
Scene Graph:
Scene
  ├── HemisphereLight          (sky/ground fill)
  ├── DirectionalLight (sun)   (shadows, golden hour)
  ├── DirectionalLight (sky)   (cool blue fill)
  ├── DirectionalLight (rim)   (atmospheric depth)
  ├── PointLight (bounce)      (green SSS simulation)
  ├── SpotLight × 12           (god rays, animated)
  ├── Terrain                  (160×160 PlaneGeometry, noise height)
  ├── Undergrowth              (80 bushes + 120 ferns)
  ├── Tree × 104               (3 depth rings, procedural)
  ├── God Ray Planes × 10      (additive blended, animated)
  └── Particles × 2000         (pollen/spore drift)
```

---

## 🔄 Workflow

```
1. Open index.html in browser (or serve locally)
2. Three.js CDN loads → WebGL context initialized
3. Procedural textures generated on canvas (no external images)
4. 104 trees procedurally placed in 3 depth rings
5. Intro camera animation: 8m → eye level (quartic ease, ~3s)
6. Wind physics loop begins → trees + particles + god rays animate
7. User scrolls → GSAP ScrollTrigger zooms camera into forest
8. Live HUD updates wind speed every 2–5 seconds
9. Globe section → 3D Earth with forest zone markers rotates
```

---

## 📈 Performance & Metrics

| Metric | Value |
|---|---|
| Total file size | Single HTML ~700 lines |
| Trees rendered | 104 (3 depth rings) |
| Particles | 2,000 (pollen system) |
| God ray spotlights | 12 animated |
| Shadow map resolution | 4096 × 4096 |
| Target frame rate | 60fps (modern GPU) |
| External assets | 0 (all procedural) |
| CDN libraries | 3 (Three.js, GSAP, Fonts) |
| Build step required | None |

---

## 🧪 Testing

```bash
# Option 1 — Open directly in browser
open index.html

# Option 2 — Serve locally (recommended for best performance)
npx serve .
# or
python -m http.server 8080
# Visit: http://localhost:8080/index.html

# Manual test checklist:
# ✅ Forest renders at 60fps on desktop
# ✅ Trees sway with wind physics
# ✅ God rays flicker through canopy
# ✅ Pollen particles drift with wind direction
# ✅ Scroll zooms camera forward into forest
# ✅ Live HUD updates wind speed every few seconds
# ✅ Globe rotates with forest zone markers visible
# ✅ Services cards drag-scroll horizontally
# ✅ Works on Chrome, Firefox, Safari, Edge
```

### Browser Compatibility

| Browser | Support |
|---|---|
| Chrome 90+ | ✅ Full |
| Firefox 88+ | ✅ Full |
| Safari 15+ | ✅ Full |
| Edge 90+ | ✅ Full |
| Mobile Chrome | ⚠️ Reduced (some features hidden) |

> **Performance tip:** On low-end devices, reduce `particleCount` (~line 350) from 2000 → 800, and tree count from 104 → 60.

---

## 📁 Project Structure

```
Forest_management/
│
├── index.html          # Entire app — HTML + CSS + JS + Three.js scene (~700 lines)
└── README.md           # This file
```

> Everything — HTML, CSS, JavaScript, Three.js scene, GSAP animations, procedural textures — lives in **one self-contained file.** No build step, no node_modules, no bundler.

---

## 🔐 Security

- **No user data collected** — fully static, no forms with data submission
- **No backend** — zero server-side attack surface
- **CDN only** — Three.js and GSAP loaded from trusted CDNs
- **GitHub Pages HTTPS** — all traffic served over SSL

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
windStrength = 0.4 + gust * 0.8;  // ← Increase multiplier for stronger wind
```

### Change Time of Day
```js
// Golden hour = 0xffe8a0 | Midday = 0xfff8f0 | Overcast = 0xb0c8d0
const sun = new THREE.DirectionalLight(0xffe8a0, 4.5);
sun.position.set(22, 18, 8);  // ← Lower Y = more dramatic shadows
```

### Change Fog Density
```js
scene.fog = new THREE.FogExp2(0x0d1f10, 0.022);  // ← Higher = denser fog
```

### Change Camera Orbit Speed
```js
camAngle += 0.0015;  // ← Increase for faster orbit
```

### Add/Remove Globe Forest Zones
```js
// [latitude, longitude] pairs
[[5,-60],[-5,20],[0,110],[55,80],[-25,-50],...]
// Add or remove entries to adjust monitored forest zones
```

---

## 🔑 Environment Variables

No environment variables required — fully static, CDN-only app.

---

## 🚀 Deployment

### GitHub Pages *(Already deployed)*

1. Push `index.html` to `main` branch
2. Go to **Settings → Pages**
3. Source: `main` branch → `/ (root)`
4. Live at: `https://manikanta-04.github.io/Forest_management/`

### Vercel / Netlify

```bash
# Drag & drop the project folder into Netlify dashboard
# OR connect GitHub repo — no build command needed
```

| Setting | Value |
|---|---|
| Framework | Other / Static |
| Build Command | *(leave empty)* |
| Output Directory | `./` |

---

## 🎨 Design System

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

## 🔮 Future Improvements

- [ ] 🌦️ Dynamic weather system — rain, storm, overcast modes
- [ ] 🦅 Wildlife — animated birds flying through canopy
- [ ] 🔥 Wildfire risk visualization layer
- [ ] 📱 Full mobile optimization with touch orbit controls
- [ ] 🌙 Day/night cycle toggle with real-time lighting transition
- [ ] 🗺️ Real GIS data integration for actual forest coordinates
- [ ] 📊 Live API integration for real CO₂ and wind sensor data
- [ ] 🎵 Ambient forest soundscape (wind, birds, leaves)

---

## 🤝 Contributing

Contributions are welcome!

```bash
# 1. Fork this repository
# 2. Create your feature branch
git checkout -b feature/your-feature-name

# 3. Commit with conventional commits
git commit -m "feat: describe your change"

# 4. Push and open a Pull Request
git push origin feature/your-feature-name
```

> Since this is a single-file project, keep all changes within `index.html` unless adding new asset files.

---

## 👨‍💻 Author

**Manikanta Naripeddi** — Full Stack & Creative Developer

[![GitHub](https://img.shields.io/badge/GitHub-Manikanta--04-181717?style=flat-square&logo=github)](https://github.com/Manikanta-04)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Manikanta%20Naripeddi-0077b5?style=flat-square&logo=linkedin)](https://www.linkedin.com/in/manikanta-naripeddi-4326232a5/)

---

## 📜 License

Built for ArborVeil Forest Intelligence. All procedural textures and geometry are generated at runtime — no third-party assets required. Licensed under the **MIT License**.

---

## 🙌 Acknowledgements

- [Three.js](https://threejs.org/) — 3D WebGL rendering engine
- [GSAP](https://gsap.com/) — Scroll animations & UI transitions
- [Google Fonts](https://fonts.google.com/) — DM Serif Display + Source Sans 3
- [GitHub Pages](https://pages.github.com/) — Free static hosting

---

<div align="center">

**Built with ❤️ for forest intelligence and immersive web experiences**

⭐ **Star this repo** if ArborVeil impressed you!

[![GitHub Stars](https://img.shields.io/github/stars/Manikanta-04/Forest_management?style=social)](https://github.com/Manikanta-04/Forest_management)

---

*🌲 The forest needs guardians. 🌿*

</div>
