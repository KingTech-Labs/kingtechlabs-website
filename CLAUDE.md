# CLAUDE.md

## Last Session (2026-04-11 ashwynd-landing-page)

**Working on:** Creating a dedicated landing page for Legends of Ashwynd at `/games/ashwynd`

**Completed:**
- Built full landing page with splash hero (Malachar art), gameplay features (2x2 grid), factions section, heroes roster, regions gallery, story section, and TestFlight CTAs
- Added all game assets: splash art, 7 hero portraits, 5 faction crests, 5 region landscapes
- Added "Eryndor Expansion" teasers in both heroes (3 mystery cards) and regions (5 mystery cards) sections
- Made Ashwynd card on main site clickable, linking to the landing page
- Restructured to `games/ashwynd/index.html` for clean URL routing on Cloudflare Pages

**Key decisions:**
- Used `object-fit: contain` for splash hero so full Malachar art is visible rather than cropped
- Used `onclick` handler on card div instead of wrapping `<a>` tag to avoid invalid nested anchor elements
- Kept Eryndor Expansion hero/region names as mysteries to build curiosity for future reveals

**Last commit:** `dbdcc04` Make Ashwynd card clickable, linking to its landing page

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
- `assets/ashwynd/` -splash art, hero portraits, faction crests, region landscapes
- `games/ashwynd/index.html` -dedicated Ashwynd landing page
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

Hosted on Cloudflare Pages, connected to GitHub repo on `master` branch. Push to deploy. No build pipeline needed.
