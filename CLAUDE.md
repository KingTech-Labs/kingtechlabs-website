# CLAUDE.md

## Last Session

**Date:** 2026-04-03

**What we worked on:**
- Minor copy fix on Legends of Ashwynd app description

**What was completed:**
- Changed "how you got there" to "how you get there" in Ashwynd description (present tense)

**Pending / next up:**
- Replace placeholder Privacy/Terms links for Legends of Ashwynd when those pages exist

**Last commit:** `d9e2d9d` Fix tense in Legends of Ashwynd description: "got" to "get"

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
