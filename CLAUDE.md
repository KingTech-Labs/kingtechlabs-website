# CLAUDE.md

## Last Session (2026-04-24 rebrand-logo-and-gold)

**Working on:** Refreshing the brand: new crowned-lion hero logo and retuned gold palette to match it

**Completed:**
- Replaced `assets/kingtechlabs-logo.png` with the new logo from `~/Downloads/KingTechLabs.png` (filename preserved so no HTML edits needed; verified only `index.html:444` references it)
- Sampled the new logo PNG with Pillow to derive the actual gold tone rather than eyeballing
- Updated brand gold across `index.html` and `games/ashwynd/index.html`: `--gold` `#eab64d` → `#edc084`, `--gold-light` `#f5ce7a` → `#f5d4a0`, and every `rgba(234, 182, 77, X)` → `rgba(237, 192, 132, X)` (including an inline Ashwynd-card accent and two faction-crest drop-shadows)
- Updated Design System note in CLAUDE.md to the new hex
- Confirmed grep clean for old `#eab64d` / `rgba(234,182,77…)` / `#f5ce7a` sitewide

**Key decisions:**
- Picked `#edc084` (the modal/most-common gold pixel in the new logo) over the brighter highlight `#f0c286` or the darker `#d6ad77` so the base color sits mid-gradient and still reads clearly on the black background
- Kept the existing `--gold-light` / `--gold-dim` / `--gold-border` variable structure instead of refactoring to gradient tokens; scope was a retune, not a system rewrite
- Left cyan `#0af7eb` (FreedomFi) and silver `#B8BEC8` untouched since neither belongs to the KingTech master brand
- Privacy/terms pages needed no changes; they don't reference the gold tokens

**Pending:**
- Swap favicons (`assets/favicon-32.png`, `assets/favicon-180.png`) once king supplies the favicon-specific image
- King is previewing the new gold in-browser and may request a warmer/lighter/darker shade

**Last commit:** `aaddac7` Retune brand gold to match new logo

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
- Gold `#edc084` -primary brand color (matches the crowned-lion logo)
- Silver `#B8BEC8` -secondary
- Cyan `#0af7eb` -FreedomFi accent
- Background: black `#000000`, cards: `#111111`

Glass-morphism navbar uses `backdrop-filter: blur`.

## Deployment

Hosted on Cloudflare Pages, connected to GitHub repo on `master` branch. Push to deploy. No build pipeline needed.
