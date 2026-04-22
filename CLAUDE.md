# CLAUDE.md

## Last Session (2026-04-22 remove-android-beta-links)

**Working on:** Removing all Android / Google Play beta links from the site since the internal-test URL only works for allowlisted email addresses

**Completed:**
- Removed "Join Google Play Beta" button from the Legends of Ashwynd app card on home `index.html`
- Removed "Join Android Beta" hero CTA, "Play on Android" story CTA, and "Join Android Beta" bottom CTA on `games/ashwynd/index.html`
- Updated supporting copy: hero subtitle now reads "Available on iOS via TestFlight"; bottom CTA copy now reads "Join the iOS beta"
- Left the FreedomFi privacy policy mention of Android biometric auth (`privacy/freedomfi.html:131`) in place since it's a generic platform reference, not a beta link

**Key decisions:**
- Did not delete the Google Play `internaltest` URL anywhere else because no other refs existed; verified with grep
- Pending item from prior session about reviewing Ashwynd privacy/terms for Android coverage is now moot since Android distribution is no longer surfaced anywhere on the site

**Pending:**
- (none)

**Last commit:** `b0b52d6` Remove Android beta links sitewide

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
