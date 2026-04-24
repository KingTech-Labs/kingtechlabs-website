# CLAUDE.md

## Last Session (2026-04-24 rebrand-logo-gold-flag-favicons)

**Working on:** Brand refresh covering a new crowned-lion hero logo, retuned gold palette, the US flag consolidated into the veteran badge, and regenerated favicons

**Completed:**
- Replaced `assets/kingtechlabs-logo.png` with the new logo from `~/Downloads/KingTechLabs.png` (filename preserved so no HTML edits needed; only `index.html:439` references it after subsequent edits)
- Sampled the new logo with Pillow to derive the actual gold rather than eyeballing
- Updated brand gold across `index.html` and `games/ashwynd/index.html`: `--gold` `#eab64d` → `#edc084`, `--gold-light` `#f5ce7a` → `#f5d4a0`, and every `rgba(234, 182, 77, X)` → `rgba(237, 192, 132, X)` (including an inline Ashwynd-card accent and two faction-crest drop-shadows)
- Updated Design System note in CLAUDE.md to the new hex; grep-verified no stale old-gold references remain
- Moved 🇺🇸 into the hero eyebrow badge at 28px (inline-styled span), removed the standalone `<div class="hero-flag">` element and its CSS rule, so the flag no longer double-renders
- Added breathing room in the hero stack: `.hero-logo` bottom margin 24px → 40px, `.hero-eyebrow` bottom margin 12px → 24px
- Regenerated `assets/favicon-32.png` and `assets/favicon-180.png` from `~/Downloads/v (3).png` with a 2200×2200 LANCZOS-downscaled crop; kept existing filenames so no HTML changes were needed
- Re-centered the favicons on the crown's symmetric axis `(2825, 1619)` instead of the bbox center `(2880, 1619)` after king flagged the lion looked too far left in the first pass

**Key decisions:**
- Picked `#edc084` (the modal/most-common gold pixel in the new logo) over the brighter highlight `#f0c286` or the darker `#d6ad77` so the base sits mid-gradient and still reads on black
- Kept the existing `--gold-light` / `--gold-dim` / `--gold-border` variable structure instead of refactoring to gradient tokens; scope was a retune, not a system rewrite
- Used an inline `font-size:28px;line-height:1` span for the badge flag rather than a new class, since the 12px badge text vs 28px flag is a one-off size mix not worth a CSS token
- Left cyan `#0af7eb` (FreedomFi) and silver `#B8BEC8` untouched since neither belongs to the KingTech master brand
- Privacy/terms pages needed no gold changes; they don't reference those tokens
- For favicon optical centering, used the crown's centroid as the reference symmetric axis rather than the full-logo bbox; the right fluffy mane and left circuit drips are asymmetric so bbox centering visibly shifts the face off-center

**Pending:**
- (none)

**Last commit:** `45e25bb` Re-center favicons on the crown axis for optical balance

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
