---
name: ui-ux-pro-max
description: AI-powered design intelligence toolkit with 192 industry rules, 79 UI styles, 192 color palettes, and typography pairings. Use whenever designing or building web apps, dashboards, landing pages, or mobile interfaces to ensure senior-level UI/UX and eliminate generic AI styling.
---

# UI/UX Pro Max Skill for Antigravity

This skill connects Antigravity to the local BM25 design intelligence engine located at `d:/Program Files/Felipe/Downloads/Agent - Kit/diseño frontend ui-ux/src/ui-ux-pro-max/scripts/search.py`.

## Credits & Author
- **Author:** [@nextlevelbuilder](https://github.com/nextlevelbuilder)
- **Repository:** https://github.com/nextlevelbuilder/ui-ux-pro-max-skill

---

## When to Use
Activate this skill whenever:
1. Designing a new user interface, landing page, mobile screen, or dashboard.
2. Selecting color palettes, typography, or component styles.
3. Defining CSS variables / design tokens.
4. Preventing generic "AI slop" (purple gradients, lack of contrast, emoji icons).

---

## Execution Workflow

Whenever a design task is requested, run the local Python search tool via `run_command`:

### 1. Complete Design System Generation (Recommended)
```bash
python "d:/Program Files/Felipe/Downloads/Agent - Kit/diseño frontend ui-ux/src/ui-ux-pro-max/scripts/search.py" "<project or industry description>" --design-system
```
*Outputs:*
- Best Landing/App Pattern
- Exact UI Style (e.g. Clean Clinical, Dark OLED, Soft UI)
- Complete Color Palette with CSS Variable names & WCAG contrast
- Font Pairing with Google Fonts import URLs
- Key Effects & GSAP animations
- Anti-patterns to strictly avoid
- Pre-delivery checklist

### 2. Specific Domain Search
```bash
# Search specific UI style
python "d:/Program Files/Felipe/Downloads/Agent - Kit/diseño frontend ui-ux/src/ui-ux-pro-max/scripts/search.py" "<query>" --domain style

# Search color palettes
python "d:/Program Files/Felipe/Downloads/Agent - Kit/diseño frontend ui-ux/src/ui-ux-pro-max/scripts/search.py" "<query>" --domain color

# Search typography
python "d:/Program Files/Felipe/Downloads/Agent - Kit/diseño frontend ui-ux/src/ui-ux-pro-max/scripts/search.py" "<query>" --domain typography

# Search UX best practices and anti-patterns
python "d:/Program Files/Felipe/Downloads/Agent - Kit/diseño frontend ui-ux/src/ui-ux-pro-max/scripts/search.py" "<query>" --domain ux
```

### 3. Stack-Specific Guidelines
```bash
python "d:/Program Files/Felipe/Downloads/Agent - Kit/diseño frontend ui-ux/src/ui-ux-pro-max/scripts/search.py" "<query>" --stack <react|html-tailwind|nextjs|vue|svelte|astro>
```
