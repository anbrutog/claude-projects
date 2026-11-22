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

**More brand references from Keith**
- YouTube channel banner (saved as `reference/youtube-banner.png`): navy gradient, heavy UPPERCASE sans headline ("WIN MORE WITH LESS STRESS... AND NO REGRETS"), red-orange brush-stroke underline, small white URL line.
- Coaching page https://www.pokerwithpresence.com/coaching (`reference/site-coaching-hero.jpg`, `site-coaching-lower.jpg`): this is the closest match to a sales page.
  - Hero: navy `#001E3A` with an orange/rust radial glow at the bottom and a lighter blue glow top right, thin orange line-art swoops at the edges, centred white Gabarito Bold headline, muted white body, solid orange button (3px radius).
  - White band with a navy Gabarito ExtraBold section heading ("Client Testimonials", "Why my coaching?").
  - Long run of testimonial cards: navy, thin light border, small radius, white text, name in bold.
  - "Why my coaching?" 3 cards on navy with an orange glow behind them; email optin on white with a light grey-blue input `#EBF0F2` and an orange button.
- Confirmed the same tokens site-wide: Gabarito only (400/500/600/700), orange `#FF3500`, navy `#001E3A`, `#EBF0F2`/`#D6DEE3`, greys `#444`/`#777`. No uppercase text on the site; uppercase shows up only on YouTube.
- Fetched page HTML was kept only in the scratchpad; screenshots are kept in `reference/` (committed).

**Draft 2 built (Keith: "Yes, go ahead with Draft 2")**
- Restyled `site/index.html` to Jason's brand, modelled on his coaching page. Copy is unchanged: a text diff against Draft 1 differs only by the old "Jason Su" text logo, now the real SVG logo.
- Section backgrounds: Hero / Full Presence proof / Guarantee = navy + orange/blue glow; Introducing PR2 + Ryan = navy-deep; letter sections, Inside PR2, Felipe, Offer, Close, FAQ = white; Bonuses + Kevin = navy; footer navy-deep with logo.
- Gabarito throughout; Playfair italic kept only for the signature. Orange buttons with 3px radius; cards 8px. Orange-deep `#D62B00` for orange text on white (contrast).
- The hero photo sits in a black panel so its black background doesn't clash with navy.
- Checked at 1440px and 390px: no horizontal scroll. Fixed the guarantee seal squashing into an oval on phone.
- CLAUDE.md design system table updated to the new tokens.
- Swoosh lines left for Framer (decorative, not import-safe).

**Side topic: Emil Kowalski skills**
- Keith wants to install `emilkowalski/skills` (aiforui.dev/skills) but use it sparingly, for finishing touches only, not auto-invoked every time.
- It's a pack of ~20 skills (main one `emil-design-eng`, ~28k chars, mostly animation/interaction polish). Correct command: `npx skills@latest add emilkowalski/skills` (the plural `skills`).
- Advice given: install only the skills needed, globally; add `disable-model-invocation: true` to each SKILL.md frontmatter so they run only when called by name (/emil-design-eng); re-apply that after updates.
- Recommended picks (from the 20 offered): `emil-design-eng`, `find-animation-opportunities`, `review-animations`. Skip mobile/Swift/Expo/Sonner and the rest. For future projects the same three are the essentials; optional later: `choreograph` (multi-element entrance sequences), `animation-performance` (if pages get animation-heavy).
- Note for PR2: the page must stay animation-free for Framer import, so on this project use the skill for motion advice to apply in Framer, not for code.
- Installed by Keith (global, in `~/.agents/skills/`, linked from `~/.claude/skills/`): emil-design-eng, find-animation-opportunities, review-animations, choreograph, animation-performance.
- `review-animations` already ships with `disable-model-invocation: true`; added that line to the other four, so all five are manual-only (`/skill-name`). Re-check after any `npx skills update`.

**Side topic: impeccable skill (impeccable.style)**
- Keith installed `impeccable` v4.10.0 globally (`~/.agents/skills/impeccable`, linked from `~/.claude/skills/`). It is currently auto-invoked and its description covers almost any frontend work, so it overlaps frontend-design / ui-ux-pro-max.
- Advice given: make it manual-only. Done: `disable-model-invocation: true` added (backup of the original SKILL.md in the session scratchpad); always call it with a command + target, e.g. `/impeccable critique site/index.html`; main commands for Keith: critique, audit, polish, plus layout/typeset when needed; leave the design-detector hook off; don't run `init`/`document` on PR2 (CLAUDE.md already holds the context); don't use `clarify` on PR2 (copy is locked).
- Suggested finishing order: impeccable critique → fixes → impeccable audit → impeccable polish → Emil skills for motion.

**Side topic: taste skill (`design-taste-frontend`, tasteskill 2.5.1)**
- Installed globally (`~/.agents/skills/design-taste-frontend`, linked from `~/.claude/skills/`). It is auto-invoked and its description claims any landing page build, redesign, polish or review.
- Heavy: 1,631 files, 31k-char SKILL.md, Node 22+ and Chrome (both present: Node v24, Chrome).
- It has a **Stop hook** in its frontmatter: once a build is armed (`.taste-skill/build.json` in the project), `gate.mjs` runs headless-Chrome checks at the end of every turn (up to 10 min) and won't let the work finish while FAILs remain. Dormant until armed; there is no `.taste-skill/` folder in this workspace.
- Its house rules conflict with PR2: it writes its own copy and lints it (60–80 words a screen), requires hover and entrance animations ("never strip"), one section per screen, its own CSS system, stand-in photos. Incompatible with locked copy, long-form DR letters and the Framer-import rules.
- Advice: make it manual-only; use it only for new brochure/company sites built from scratch (e.g. local-business audit mockups), never on PR2 or other DR sales pages. Keith said yes: added `disable-model-invocation: true` after the `name:` line (the description is a multi-line block). YAML validated; original backed up in the session scratchpad. Invoke with `/design-taste-frontend`.

**Next**
- Keith to review Draft 2. Then price/checkout. Still to get: PR2 product logo/mockup (Draft 2), plus the price and checkout platform.
