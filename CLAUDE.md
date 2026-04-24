# CLAUDE.md

## Last Session (2026-04-24 copy-veteran-hyphen-and-android-positioning)

**Working on:** Tightening positioning copy: hyphenating "Veteran-Owned" as a compound modifier and broadening studio/product copy from iOS-only to "iOS and Android" ahead of FreedomFi's Android launch

**Completed:**
- `index.html`: hero eyebrow `Veteran Owned & Operated` → `Veteran-Owned & Operated` (line 440); About copy `veteran owned & operated` → `veteran-owned & operated` (line 540)
- `index.html`: meta description `Independent iOS apps` → `Independent iOS and Android apps` (line 6); hero sub `iOS apps` → `iOS and Android apps` (line 442); About `iOS studio` → `iOS and Android studio` (line 540)
- `terms/freedomfi.html`: third-party service outages list now includes Google Play Store and Android Keystore (line 194); compatibility clause now reads "iOS or Android" (line 196)
- Logged the remaining pre-Android-launch FreedomFi terms sweep (lines 142, 144–146, 149, 170, 173, 183–187, 191, 228, 237) as a TODO under "Pending / Next Up" in `~/claudecode/FreedomFi/CLAUDE.md` so it surfaces in the right repo

**Key decisions:**
- Did NOT touch the Ashwynd page's "iOS Beta / TestFlight" references because Ashwynd's beta is genuinely iOS-only; broadening that copy would be inaccurate
- Did NOT touch `privacy/freedomfi.html:131` biometric clause since it already covers Face ID / Touch ID / Android fingerprint
- Did NOT do the full FreedomFi terms Apple→multi-platform sweep here. Apple's required EULA boilerplate (sections 142, 144–146, 237) must stay but be scoped to "App Store distribution" with parallel Google Play language; that's lawyer-review work, not a copy tweak. Logged in FreedomFi CLAUDE.md instead
- "Veteran-Owned" hyphen is the compound-modifier form (correct grammar before a noun); does not violate the global no-hyphen-as-pause rule

**Pending:**
- Pre-Android-launch legal copy sweep on `terms/freedomfi.html` (full detail logged in `~/claudecode/FreedomFi/CLAUDE.md` Pending section)

**Last commit:** `b6ef0db` Hyphenate Veteran-Owned and broaden positioning to iOS and Android

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
