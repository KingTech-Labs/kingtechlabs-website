# CLAUDE.md

## Last Session

**Date:** 2026-03-22

**What we worked on:**
- Added a Terms of Service page for FreedomFi
- FreedomFi app card UI polish on the homepage
- Coming Soon card layout update
- Project-level /wrap skill setup

**What was completed:**
- Created `terms/freedomfi.html`: full ToS page matching the privacy policy design (dark theme, cyan highlight borders changed to full border)
- Updated highlight/warning box borders on both `privacy/freedomfi.html` and `terms/freedomfi.html` to full border instead of left-side only
- Moved Privacy Policy and Terms of Service links into the FreedomFi app card (removed from footer), centered
- Moved Beta pill above Join TestFlight link, both centered in the card footer
- Updated Coming Soon card to match FreedomFi card structure (same layout, gold accent, lightbulb icon, placeholder legal links)
- Created `.claude/commands/wrap.md`: project-level /wrap skill (2 steps only, website-specific)

**Pending / next up:**
- Nothing outstanding

**Decisions made:**
- KingTech Labs is a Massachusetts LLC (not Texas); governs ToS
- "tracking" is acceptable in legal/ToS context; avoid it only in marketing copy
- Legal links (Privacy Policy, Terms of Service) live in the app card, not the site footer
- /wrap project skill takes precedence over global wrap for this repo (takes effect next session)

**Last commit:** 3f69c69

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
