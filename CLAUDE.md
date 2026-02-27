# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Static marketing website for Village Residential LLC — a woman-owned general contracting company based in Raleigh, NC. No build system, bundler, or package manager. Open HTML files directly in a browser to preview.

**Live site:** https://villageresidential.co/

## Architecture

Plain HTML/CSS/JS — three pages share one stylesheet:

- `index.html` — Home page (hero, services grid, about preview, before/after project gallery, CTA)
- `about.html` — Company story and values
- `contact.html` — Contact form (Formspree) and contact details
- `style.css` — Single stylesheet for all three pages

Project photos live in `project-1-before/` and `project-1-after/` as JPGs.

## Design System

All defined in CSS custom properties at the top of `style.css`:

| Variable | Value | Use |
|---|---|---|
| `--accent` | `#b09080` | Warm taupe — primary brand color, icons, highlights |
| `--black` | `#302e2d` | Primary text, dark backgrounds |
| `--charcoal` | `#3e3a38` | Hero/nav backgrounds |
| `--light-grey` | `#f6f5f3` | Alternate section backgrounds |

**Typography:** Georgia/serif for headings (`h1`–`h4`), Inter/sans-serif for body and UI. Fluid heading sizes use `clamp()`.

**Layout:** `.container` centers content at 90% width, max 1100px.

**Breakpoints:** `768px` (stacks grids, shows hamburger nav), `600px` (single-column flip grid).

## Key Patterns

**Navigation:** Duplicated verbatim across all three pages. Set `class="active"` on the current page's `<a>` tag. Mobile toggle uses `toggleNav()` which adds/removes `.open` on `#navLinks`.

**Before/After gallery:** CSS opacity crossfade (no 3D flip). `.flip-card-front` starts at `opacity: 1`, `.flip-card-back` at `opacity: 0`. Hover triggers via CSS; tap toggles `.flipped` class via JS click handler (index.html only).

**Contact form:** Uses Formspree. The `action` attribute in `contact.html:124` contains a placeholder `YOUR_FORM_ID` — replace with an actual Formspree endpoint before the form will work. A hidden honeypot field (`name="_gotcha"`) handles spam.

**Sections:** Added as new `<section>` blocks. Each page section follows the pattern: `.section-label` (small caps eyebrow) → `h2.section-title` → content.
