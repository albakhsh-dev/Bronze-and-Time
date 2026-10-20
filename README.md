# Laocoön — Bronze and Time

> An immersive, cinematic WebGL experience featuring a 360° orbital camera, procedural liquid-metal GLSL wave shaders, dynamic forge spark physics, and luxury editorial typography.

![License: MIT](https://img.shields.io/badge/License-MIT-gold.svg)
![Three.js](https://img.shields.io/badge/Three.js-r0.160-black?logo=three.js)
![WebGL](https://img.shields.io/badge/WebGL-2.0-red?logo=webgl)
![GLSL](https://img.shields.io/badge/Shaders-GLSL-blue)

---

## ✦ Overview

**"Bronze and Time"** is a creative front-end experiment that merges classical museum sculpture with modern digital creative direction. Centered on a noble, semi-polished bronze horse statue rendered in WebGL on a deep-black chiaroscuro stage, the entire experience is orchestrated by smooth, physics-lerped scroll dynamics across four editorial chapters.

### Key Highlights
- **Single Self-Contained Architecture**: Zero bundlers, zero build steps, and zero frameworks. Built with modern ES Modules and native browser capabilities.
- **Custom Liquid-Bronze GLSL Fragment Shader**: Screen-space procedural wave synthesis with 3D noise deformation that evolves dynamically from molten bronze (`#080401`) to deep sapphire blue (`#04091a`) as you scroll.
- **Theatrical Chiaroscuro Lighting Rig**: Physically-based rendering (PBR) tuned with a high-intensity key spotlight with PCF soft shadows, cool icy-blue rim directional lighting, and warm floor fill.
- **450 Particle Forge Sparks**: Additive-blended point cloud with real-time velocity turbulence acceleration when scrolling rapidly.
- **Universal Scroll & Interaction Engine**: Supports mouse wheel with physical inertia lerp, touch swipe gestures, keyboard navigation (arrows/space/page keys), and click-and-drag viewport orbital control.
- **Editorial Micro-interactions**: Per-letter blur-up animation (`filter: blur(12px) → 0`), stories-style segmented progress bar, vertical grid lines with drifting dots, and a custom magnetic dual-ring cursor.

---

## ✦ Technology Stack

| Domain | Technology |
| :--- | :--- |
| **3D & Rendering** | [Three.js](https://threejs.org/) (r0.160) via CDN Importmap, WebGL 2.0 |
| **Shaders** | Custom GLSL Vertex & Fragment Shaders |
| **3D Assets** | High-precision GLTF/GLB models with custom PBR material overrides |
| **Typography** | Google Fonts (*Italiana*, *Outfit*, *Playfair Display*) |
| **Styling & Layout** | Pure Vanilla CSS3, Grid overlays, CSS `clip-path` animations |

---

## ✦ How to Run Locally

You can preview the project instantly without installing dependencies:

### Option 1: Direct File
Simply double-click `index.html` to open it in Chrome, Edge, Safari, or Firefox.

### Option 2: Local HTTP Server (Recommended)
Using Python's built-in web server:
```bash
# Python 3
python -m http.server 8080
```
Open `http://localhost:8080/index.html` in your browser.

Using Node.js:
```bash
npx serve .
```



## ✦ Design & Engineering Details

### 1. Camera Choreography
The camera trajectory follows a parametric 360° orbit:
$$\phi = \text{scroll} \times 2\pi$$
$$y = 0.35 + \sin(\text{scroll} \cdot \pi) \times 0.8$$
$$\text{radius} = 4.2 - \sin(\text{scroll} \cdot \pi) \times 0.6$$
During the initial chapter ($0.0 \le \text{scroll} \le 0.28$), the look-at target eases with an offset (`-0.9 * easeFactor`) to intentionally push the statue into the golden ratio of the right viewport, clearing space for the editorial typography on the left.

### 2. GLSL Procedural Wave Field
The background shader synthesizes 3 intersecting harmonic sine waves warped through a 3D hash noise function:
```glsl
float w1 = sin(dot(warpedUv, dir1) * freq1 + time * 1.0);
float w2 = cos(dot(warpedUv, dir2) * freq2 - time * 1.4 + w1 * 0.4);
float w3 = sin(dot(warpedUv, dir3) * freq3 + time * 1.8 + w2 * 0.5);
float waveField = w1 * 0.50 + w2 * 0.35 + w3 * 0.15;
```

---

## ✦ License

MIT License — Feel free to customize and showcase in your personal portfolio!
