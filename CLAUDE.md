# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

A collection of self-contained web projects served via XAMPP on localhost. Most projects are a single HTML file; a few are directories with an `index.html`. There is no build, compile, or install step.

## Serving

XAMPP must be running (Apache). Access projects at:
```
http://localhost/sites/claude/<filename>.html       # single-file project
http://localhost/sites/claude/<directory>/          # directory project
```

## Current Projects

| Path | Description |
|------|-------------|
| `tictactoe.html` | Two-player Tic Tac Toe — dark UI, score tracking, win animations |
| `complyloft/index.html` | ComplyLoft homepage — enterprise compliance automation platform |
| `complyloft/final/index.html` | ComplyLoft homepage v2 — corner brackets, pixel-art SVG icons, hamburger nav |
| `complyloft/prop/index.html` | 15-slide marketing proposal deck for bestsalesfunnels.net |
| `argus/index.html` | Argus — niche trend-tracking landing page |
| `report/index.html` | Anthropic News Report (April 2026) |
| `firsttest/index.html` | Marketing Camelot — Doberman Dan |
| `the-four-systems/` | Four-SEO-skills dashboard (keyword research, content, links, tracking) |
| `binauralbreathing/index.html` | Binaural Breathing — app landing page; light theme + selective dark sections; Web Audio API binaural player in sessions section |
| `next-app/` | Next.js app — has `node_modules`, needs `npm run dev` (see note below) |

## Repository Conventions

- Each project is a **single self-contained HTML file** — all CSS in `<style>`, all JS in `<script>`, no CDN/npm.
- Directory projects (`complyloft/`, `argus/`, etc.) use `index.html` inside a folder but are still self-contained.
- `next-app/` is the exception — it is a full Next.js project. Run with `npm run dev` from that directory; it does **not** serve via XAMPP.
- Commit messages follow Conventional Commits: `feat:`, `fix:`, `style:`, `refactor:`, `chore:`.
- Commit and push after every logical unit of work — never batch unrelated changes, never leave a session without pushing.

```bash
git add <file>
git commit -m "feat: description"
git push
```

## Design Systems

Projects each have their own design system. Do not carry tokens across projects.

### ComplyLoft (`complyloft/`)

Brand-accurate design system — do not deviate from these tokens:

| Token | Value |
|-------|-------|
| Font | Rubik (400/500/600/700/800) via Google Fonts |
| Primary accent | `#5910F8` (purple); hover `#6B24FF` |
| Accent light | `#F3EFFE` (optin bg, featured-card tint) |
| Dark / primary | `#040A17` |
| Border radius | **0px** on all containers, cards, inputs; **6px** on buttons only |
| Secondary button | `#040A17` bg · `#E8E0FD` text · `#E8E0FD` border |

Product: document auditing automation, PII redaction, accessible PDF remediation.

### ComplyLoft Proposal (`complyloft/prop/index.html`)

15-slide JS-driven presentation for bestsalesfunnels.net. Uses `position:absolute` + `.active`/`.out` CSS transitions. Each slide has a base64-embedded watermark logo; slide 2 has a base64 portrait photo.

| Token | Value |
|-------|-------|
| Font | Inter (300–900) via Google Fonts |
| Dark / primary | `#000000` pure black (Uber B&W aesthetic) |
| Accent | `#ed9b33` amber — sole colour accent |
| Bg-light | `#f5f5f5` |
| Page surround | `#111111` |
| Border radius | **0px** containers, cards, step numbers, nav buttons; **2px** on badges and tags only |

Do not introduce additional colours. Amber is the only non-black/white element.

### Binaural Breathing (`binauralbreathing/`)

Light theme with selective dark sections. Do not deviate:

| Token | Value |
|-------|-------|
| Font | Inter only (no second typeface) |
| Primary accent | `#ED1654` (pink); hover `#D41249` |
| Secondary accent | `#00ACEE` (cyan) |
| Near-black | `#171717` (dark sections + headings) |
| Background | `#FFFFFF`; surface `#F7F7F7`; mid `#F2F2F2` |
| Hero background | `#0F0F0F` (dark, not rebrandable) |
| Container radius | **0px**; button radius **6px** |

Dark sections use `.section-dark` utility class: how-it-works, sessions, community, science, final-cta.

`blueprint/style.html` — Lawrence van Lingen Shopify page kept as typography reference. Do not delete.

### Tictactoe (`tictactoe.html`)

| Token | Value |
|-------|-------|
| Background | `#0f0f13` |
| Surface | `#1a1a24` |
| Border | `#2a2a38` |
| X accent | `#7c6af7` (purple) |
| O accent | `#f97a6a` (coral) |
| Font | `'Segoe UI', system-ui, -apple-system, sans-serif` |
| Radius | Cards 16px · cells/inputs 12px |

## Frontend Design Workflow

For new or redesigned pages, invoke the `frontend-design` skill. It encodes:
- Full CSS custom property token system (`:root` block)
- Component patterns: buttons, cards (light/dark/featured), floating badge, sticky nav, grids, scroll reveal, email optin form
- Accessibility baseline (skip link, `aria-labelledby`, `role="list"`, `prefers-reduced-motion`)
- Pre-delivery checklist

The skill requires `ui-ux-pro-max` to be run first (with `--design-system`) to generate the design system when starting a new project.

## Accessibility Baseline (all projects)

- `<a href="#main-content" class="skip-link">` as first element in `<body>`
- `<main id="main-content">` wraps page content
- `aria-labelledby="heading-id"` on every `<section>`
- `aria-label` on every `<nav>` and `<footer>`
- No emoji as icons — inline SVG only (Heroicons / Lucide paths)
- `prefers-reduced-motion` handled on all animations
