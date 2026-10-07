---
name: scroll-world
description: Builds immersive, scroll-scrubbed "fly through the world" landing pages with seamless continuous camera flight (Apple/Emons style) using pre-rendered video scrubbing and Vanilla JS engine.
---

# Scroll World Skill for Antigravity

This skill provides guidelines and engine assets for building continuous 3D scroll-scrubbed landing pages without framerate drops or heavy runtime 3D overhead.

## Credits & Author
- **Author:** [@oso95](https://github.com/oso95)
- **Repository:** https://github.com/oso95/scroll-world
- **Local Engine Assets:** `d:/Program Files/Felipe/Downloads/Agent - Kit/diseño frontend 3d/skills/scroll-world/references/`

---

## When to Use
Use when:
1. The user asks for a 3D diorama or cinematic scroll-through landing page.
2. A product showcase needs to dive continuously into different scenes with zero cuts/jumps.
3. High-performance scroll animation is required (using pre-rendered scrubbing rather than heavy WebGL/Three.js).

---

## Key Rules for Senior Execution
1. **Frame-Locking (The Golden Rule):** The last frame of clip $N$ must be pixel-identical to the first frame of connector clip $N+1$ to avoid visible pops.
2. **Style Preamble:** Maintain identical style preamble across all scene prompts for lighting and color consistency.
3. **Vanilla JS Engine:** Utilize `d:/Program Files/Felipe/Downloads/Agent - Kit/diseño frontend 3d/skills/scroll-world/references/scrub-engine.js` with `requestAnimationFrame` and seek-coalescing.
