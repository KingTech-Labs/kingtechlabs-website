# CLAUDE.md

## Last Session (2026-04-22 google-play-beta-links)

**Working on:** Adding Google Play internal test links alongside existing TestFlight links for Legends of Ashwynd

**Completed:**
- Added Google Play Beta link to the Ashwynd card on main `index.html`
- Added Android Beta CTA beside all three TestFlight CTAs on `games/ashwynd/index.html` (hero, story, bottom CTA)
- Updated hero platform caption to mention both iOS and Android availability
- Relabeled "Join the Beta" / "Play the Beta Now" / "Join TestFlight" CTAs to explicitly say iOS/Android
- Centered the hero CTA pair (the flex wrapper was inheriting `text-align: center` but flex children needed `justify-content: center`)

**Key decisions:**
- Reused the existing `hero-cta` gold style for the Android button rather than introducing a second color, keeping visual parity between the two platforms
- Wrapped paired CTAs in a `flex-wrap` container so they stack cleanly on narrow screens

**Pending:**
- Review `privacy/legendsofashwynd.html` and `terms/legendsofashwynd.html` to confirm they cover Android / Google Play distribution, not just iOS / TestFlight

**Last commit:** `f122319` Center hero beta CTA buttons on Ashwynd page

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
