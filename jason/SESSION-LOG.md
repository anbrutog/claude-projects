# PR2 Sales Page: session log

Running record of what was discussed and decided in each Claude Code session. Newest at the top. Read this together with `CLAUDE.md` at the start of every session, and add to it as work happens.

---

## 22 Nov 2026: Session 1 (project folder review)

**State of the folder at start**
- Only `CLAUDE.md`, `COPY-ISSUES.md` and `pr2-sales-page-handover.zip` are in `jason/`.
- The actual build (`site/index.html`, `site/img/*`, `copy/PR2_copy.md`, `copy/PR2_copy_original.docx`, `README.md`) is still inside the zip, under a `pr2-sales-page/` folder. Not unpacked yet.
- `CLAUDE.md` in the folder is identical to the one in the zip. `COPY-ISSUES.md` (12 items) sits at the root here, while `CLAUDE.md` expects it at `copy/COPY-ISSUES.md`.
- `jason/` is not yet tracked in git.

**Requests from Keith**
- Keep a running memory of the conversation as we go (this file).

**Decisions**
- Keith OK'd unpacking the zip and committing/pushing `jason/` (including Jason's photos and copy) to the `sites/claude` repo.

**Done**
- Unpacked the zip into `jason/`: `site/`, `copy/` and `README.md` now sit at the top level, matching `CLAUDE.md`.
- Moved `COPY-ISSUES.md` into `copy/` (it was identical to the zip's copy).
- Kept the local `CLAUDE.md`, which adds a pointer to this log. The zip's version was otherwise identical.
- The zip is kept locally but not committed, since its contents are now in the repo.
- Committed and pushed `jason/`.

**Logo attempt 1**
- Keith pasted a snippet copied from Jason's site (looks like a Framer export): `<svg viewBox="0 0 1393 280"><use href="#svg-169048601_5268"></use></svg>`.
- It only references a symbol defined elsewhere on the page, so it holds no logo artwork. The one useful detail is the shape: 1393×280, roughly 5:1, so a horizontal wordmark.
- Asked Keith for the actual file (SVG preferred, else a transparent PNG) or the URL of Jason's site so the symbol can be pulled from it.

**Logo attempt 2: done**
- Keith gave Jason's site: https://www.pokerwithpresence.com/ (a Framer site). Pulled the full logo SVG (symbol `svg-169048601_5268`) from the page.
- Saved as `site/img/brand/jason-su-logo-light.svg` (white wordmark, for dark backgrounds) and `jason-su-logo-dark.svg` (black wordmark, for light backgrounds). The "S" mark is orange `#FF3500` in both.
- Gotcha: part of the lettering in the source had an inline `style="fill:#fff"`, so it disappeared on white. Removed it, and both versions were checked visually.

**Brand found on Jason's site (not applied yet, awaiting Keith's direction)**
- Colours: orange `#FF3500` (primary, buttons/CTAs), navy `#001E3A` (hero/dark background), light grey-blue `#EBF0F2` / `#D6DEE3` (light surfaces, inputs), white, greys `#444` / `#777`.
- Fonts: **Gabarito** (main font: headings, body, buttons; weights 400/500/600), plus Playfair and Inter in small amounts. All are Google Fonts.
- Look: navy hero with orange line-art swoops and a glow, white text, solid orange buttons with small radius.
- This is quite different from the provisional Draft 1 system (black/cream/gold, Playfair + Source Serif). Asked Keith whether Draft 2 should match the site.

**Next**
- Waiting on Keith: decision on brand direction, then price/checkout. Logo is in hand. Still to get: PR2 product logo/mockup (Draft 2), plus the price and checkout platform.
