# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

RECBOSS & CAFE is a static marketing website for a senior fitness center in Ryugasaki, Japan. The entire site lives in a single file: `index.html`. There is no build process, no package manager, and no server-side code.

## Running the Site

Open `index.html` directly in a browser, or serve it with any static HTTP server:

```bash
# Python
python3 -m http.server 8000

# Node (if npx is available)
npx serve .
```

No compilation, installation, or environment variables required.

## Architecture: Single-File Structure

All code is in `index.html` (~941 lines), organized in this order:

1. **`<head>`** (lines 1–18) — meta tags, OG tags, Google Fonts
2. **`<style>`** (lines 19–519) — all CSS, including CSS custom properties and media queries
3. **`<body>`** (lines 520–910) — 11 page sections (header, hero, features, schedule, pricing, cafe menu, gallery, reviews, access, FAQ, footer)
4. **`<script>`** (lines 912–939) — vanilla JS for font-size toggle, mobile nav, scroll-reveal, FAQ accordion

## CSS Conventions

CSS custom properties are defined on `:root`:

| Variable | Value | Role |
|---|---|---|
| `--primary` | `#4a9d6e` | Main green (buttons, accents) |
| `--primary-dark` | `#3d8259` | Hover states |
| `--primary-soft` | `#dcefe2` | Section backgrounds |
| `--primary-pale` | `#f1f9f4` | Alternate backgrounds |
| `--accent` | `#f5a623` | Orange highlights (badges) |

Always use these variables rather than hardcoding color values.

## Key External Dependencies

- **Booking form**: hosted at `https://rad-sopapillas-4a7d91.netlify.app/` (linked from CTA buttons)
- **Instagram**: `https://www.instagram.com/ryugasaki_recboss`
- **Images**: Unsplash CDN URLs (hero, gallery)
- **Fonts**: Google Fonts (Zen Maru Gothic, Noto Sans JP)
- **Map**: Google Maps embed in the access section

## Editing Guidance

- **Content changes** (text, prices, hours) — edit directly in the HTML body sections.
- **Style changes** — edit within `<style>` or update CSS variables on `:root`.
- **Behavior changes** — edit within `<script>` at the bottom of the file.
- The site targets elderly Japanese users: preserve large base font sizes (`font-size: 18px` on `body`), high contrast ratios, and the font-size toggle feature (`.font-small` / `.font-large` classes applied to `<html>`).
- `prefers-reduced-motion` is respected in the scroll-reveal JS — keep this intact.

## Business Content Reference

| Section | Key Details |
|---|---|
| Schedule | Tue & Fri, 10:00–11:00 and 13:00–15:00 |
| Plans | Free trial / ¥6,800 monthly / ¥4,980 weekly / ¥1,100 per visit |
| Cafe menu | 6 items (soups, rice, yogurt, coffee, tea, dried sweet potato) |
| Phone | Displayed in header |
| Address | Ryugasaki, Ibaraki prefecture |
