# CLAUDE.md

## Last Session

**Date:** 2026-03-22

**What we worked on:**
- Hero section UI polish: Veteran-Owned text, American flag, and logo spacing

**What was completed:**
- Added 🇺🇸 emoji below "Veteran-Owned iOS Studio" text in the hero (`index.html`)
- Removed pill styling from `.hero-eyebrow`; now plain gold text only (no background, border, border-radius, or padding)
- Added `.hero-flag` CSS class (font-size: 28px, sits between eyebrow and h1)
- Reduced `.hero-logo` bottom margin from 40px to 24px to tighten space under the lion logo

**Pending / next up:**
- Nothing outstanding

**Decisions made:**
- Flag rendered as emoji, not SVG/image asset
- "Veteran-Owned iOS Studio" is plain gold text, no pill/badge container

**Last commit:** e300c2a

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
