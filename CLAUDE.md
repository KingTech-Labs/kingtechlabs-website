# CLAUDE.md

## Last Session

**Date:** 2026-03-21

**What we worked on:**
Copywriting review and wording change in the Education section of index.html.

**What was completed:**
- Changed the Education section headline from "We don't just track. We teach." to "We don't just build tools. We teach."
- Reason: "track" had privacy-adjacent connotations that could be misread in the context of a finance app
- New wording is broader, reflects the studio's overall philosophy, and has no privacy baggage

**Pending / next up:**
- Nothing outstanding from this session

**Decisions made:**
- Avoid the word "track" anywhere on the site given the privacy-first brand positioning of FreedomFi

**Last commit:** 8c9b687

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

## Design System

CSS variables defined at the top of the `<style>` block:
- Gold `#eab64d` -primary brand color
- Silver `#B8BEC8` -secondary
- Cyan `#0af7eb` -FreedomFi accent
- Background: black `#000000`, cards: `#111111`

Glass-morphism navbar uses `backdrop-filter: blur`.

## Deployment

Static hosting -push to GitHub, deploy via GitHub Pages, Netlify, Vercel, or any CDN. No build pipeline needed.
