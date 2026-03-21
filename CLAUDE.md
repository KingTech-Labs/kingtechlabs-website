# CLAUDE.md

## Last Session

**Date:** 2026-03-21

**What we worked on:**
- Education section copywriting review
- Created the /wrap skill and set it up for this website project

**What was completed:**
- Changed Education headline from "We don't just track. We teach." to "We don't just build tools. We teach.":removed "track" due to privacy connotation concerns
- Added CLAUDE.md to the repo (was previously untracked)
- Created and configured the /wrap skill at ~/.claude/commands/wrap.md, removing the OTA update reference so it's website-specific
- Noted: pre-commit hook on this repo rejects em dashes:use regular hyphens in all committed files

**Pending / next up:**
- Nothing outstanding

**Decisions made:**
- Avoid the word "track" on the site given FreedomFi's privacy-first positioning
- /wrap skill is now the standard session close for this project

**Last commit:** 43cae85

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
