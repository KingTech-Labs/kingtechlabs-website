# CLAUDE.md

## Last Session (2026-04-24 replace-company-logo)

**Working on:** Swapping the hero logo with a new crowned-lion mark provided by king

**Completed:**
- Replaced `assets/kingtechlabs-logo.png` with the new logo from `~/Downloads/KingTechLabs.png` (filename kept identical so no HTML edits needed)
- Verified only one HTML reference existed (`index.html:444`); favicons left untouched per king's instruction

**Key decisions:**
- Did not regenerate favicons since king said he'll provide a separate favicon image later; the new logo's whitespace and "LABS" wordmark wouldn't scale well to 32×32 anyway
- Kept the original filename rather than introducing a versioned name to avoid touching HTML and cache-busting logic

**Pending:**
- Swap favicons (`assets/favicon-32.png`, `assets/favicon-180.png`) once king supplies the favicon-specific image

**Last commit:** `209487f` Replace hero logo with new crowned lion mark

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
