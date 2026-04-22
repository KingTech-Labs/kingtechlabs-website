# CLAUDE.md

## Last Session (2026-04-22 ashwynd-hero-names)

**Working on:** Adding hero names above class labels on the Ashwynd heroes roster, with per-class colors

**Completed:**
- Added `.hero-name` CSS rule (gold, 16px, bold) and restyled `.hero-class` as a smaller uppercase letter-spaced subtitle
- Added hero names above each class on `games/ashwynd/index.html`: Sir Roland (Knight), Selene Moonveil (Mage), Finn Hawke (Archer), Zara Blackwell (Rogue), Azrael Valorian (Paladin), Brother Thorne (Inquisitor), Mortis the Hollow (Necromancer)
- Applied per-class colors to each class label via inline styles (cobalt, violet, forest, bronze, holy gold, crimson, sickly green)

**Key decisions:**
- Used inline `style="color: #…"` on each class div rather than per-class CSS modifiers, since each hero color is a one-off and adding seven class rules for single-use colors would be noisier than the inline approach
- Kept hero name in brand gold so the roster still reads as a cohesive KingTech visual; only the class label varies in color

**Pending:**
- Review `privacy/legendsofashwynd.html` and `terms/legendsofashwynd.html` to confirm they cover Android / Google Play distribution, not just iOS / TestFlight

**Last commit:** `1a06efa` Add hero names and class-colored labels to Ashwynd roster

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
