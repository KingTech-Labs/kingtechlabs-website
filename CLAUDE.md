# CLAUDE.md

## Last Session (2026-04-04 ashwynd-beta-styling)

**Working on:** Updating Legends of Ashwynd card to reflect beta status with matching styling

**Completed:**
- Changed Ashwynd card badge from `badge-dev` / "In Development" to `badge-beta` / "Beta"
- Added "TestFlight coming soon" note below the badge
- Changed card accent color from red (`#c0392b`) to gold (`#eab64d`) to match the beta badge and brand color

**Pending:**
- Update TestFlight link once app review is approved

**Last commit:** `7e12441` Change Legends of Ashwynd card accent from red to gold to match beta badge

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
- `privacy/legendsofashwynd.html` -standalone privacy policy page for Legends of Ashwynd
- `terms/freedomfi.html` -standalone terms of service page for FreedomFi
- `terms/legendsofashwynd.html` -standalone terms of service page for Legends of Ashwynd

## Design System

CSS variables defined at the top of the `<style>` block:
- Gold `#eab64d` -primary brand color
- Silver `#B8BEC8` -secondary
- Cyan `#0af7eb` -FreedomFi accent
- Background: black `#000000`, cards: `#111111`

Glass-morphism navbar uses `backdrop-filter: blur`.

## Deployment

Static hosting -push to GitHub, deploy via GitHub Pages, Netlify, Vercel, or any CDN. No build pipeline needed.
