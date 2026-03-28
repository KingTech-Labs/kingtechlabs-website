# CLAUDE.md

## Last Session

**Date:** 2026-03-28

**What we worked on:**
- Added Legends of Ashwynd app card to the apps section

**What was completed:**
- Replaced the Coming Soon placeholder card with a real Legends of Ashwynd card
- Added icon (`assets/legends-of-ashwynd-icon.png`) from user-provided image
- Card uses crimson accent color (`#c0392b`) to match the dark fantasy icon palette
- Full description text, Dark Fantasy RPG category, In Development badge, placeholder Privacy/Terms links

**Pending / next up:**
- Replace placeholder Privacy/Terms links when those pages exist

**Decisions made:**
- Card is not styled as `coming-soon` (no faded/dashed treatment) since it's a named real project
- Kept placeholder Privacy/Terms links per user request

**Last commit:** e7a90e4

---

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

KingTech Labs is a veteran-owned indie iOS studio. This is a **static single-page marketing website** -no build tools, no frameworks, no dependencies.

## Development

Serve the site locally with any static HTTP server:
```bash
python3 -m http.server 8000
```
Then open `http://localhost:8000`.

No build step, no npm install, no compilation required.

## Architecture

Everything lives in `index.html`:
- All CSS is embedded in a single `<style>` block (~16KB)
- No external CSS, JS libraries, or CDN resources
- The site is fully self-contained

**Supporting files:**
- `assets/` -logo, app icons, favicons
- `privacy/freedomfi.html` -standalone privacy policy page for FreedomFi
- `terms/freedomfi.html` -standalone terms of service page for FreedomFi

## Design System

CSS variables defined at the top of the `<style>` block:
- Gold `#eab64d` -primary brand color
- Silver `#B8BEC8` -secondary
- Cyan `#0af7eb` -FreedomFi accent
- Background: black `#000000`, cards: `#111111`

Glass-morphism navbar uses `backdrop-filter: blur`.

## Deployment

Static hosting -push to GitHub, deploy via GitHub Pages, Netlify, Vercel, or any CDN. No build pipeline needed.
