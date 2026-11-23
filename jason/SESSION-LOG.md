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

**Russell Brunson skill applied (Draft 2.1)**
- Keith asked to use the `russell-brunson-landing-page` skill on the page, keeping fonts and colours the same.
- Applied the skill's design patterns only, in brand colours: doodle underlines under 9 labels (flex shrink-wrap + `width:0;min-width:100%` SVG trick instead of `display:table`, to stay flexbox-only); doodle arrows either side of 2 CTAs (flex row, hidden under 900px); 3 dotted-chevron dividers; an "Everything you get" offer-stack box in the Offer section.
- Not applied, and why: Bebas Neue/Work Sans/red/gold buttons (brand kept); hover effects (no motion, Framer); urgency section and "Your Host" bio (no copy for them, and no fake urgency); credibility logo bar (no logos); generated device mockup (waiting on the real PR2 mockup); hero CTA (would interrupt the hook; possible option).
- Copy check against Draft 2: nothing removed or changed; only the stack's text was added (titles verbatim, values normalised).
- Checked at 1440 and 390: doodles match label widths exactly, arrows hidden on phone, no horizontal scroll.

**Keith's feedback on the RB pass**
- Keith didn't recognise "the stack" and said: "Absolutely nothing should change in terms of design, it should be the exact same." Removed the offer-stack box, its CSS and the chevron that came with it. Lesson: don't add new sections or content blocks; only decorate existing content.
- Kept the doodle underlines, arrows and 2 chevrons for now, and asked Keith to confirm whether they stay.
- Keith said yes to a hero button: added "Join Now And Receive Instant, Lifetime Access To PR2" (existing CTA wording) below "Elite Poker Performance", linking to `#join`. Left-aligned on desktop, full width on phone.
- Text diff vs Draft 2: only the hero button text added.
- Keith then confirmed: **keep the doodles/arrows/chevrons**, and **add the stack back** (he likes it even though it adds new copy). Restored the stack HTML and CSS exactly as in commit 7b52a9d, alongside the new hero button. Original copy unchanged; checked 760px wide on desktop, 8 rows, total $11,391, no phone overflow.

**Hero refinement: modelled on Dan Kennedy's Magnetic Marketing hero (Keith's screenshot)**
- Keith wants the hero to resemble the Magnetic Marketing hero, done step by step. Step 1: the headline.
- The headline is split into 3 sizes with no words changed (same h1, three spans): small white lead-in "Why Do So Many … Train Them In" (28px) → huge orange **"Full Presence"** (80px, weight 900) → medium white "After Having Worked With The Other Top Coaches?" (34px). Then a 4px orange rule underneath, like their red line.
- Sizes: key 80px desktop, 62px at ≤1200px (incl. tablet), 50px phone. Checked "Full Presence" stays on one line at 1440, 1200, 1100, 1001, 1000, 810, 640 and 390. h1 text is identical to before.
- Alternative emphasis offered: make "World Series And Triton Champions" the big line instead.
- Step 2: Jason in front of a circle, like Dan Kennedy, and moved up beside the copy.
  - The circle uses brand orange `#FF3500` (fading to `#D62B00` at the edge), since colours stay the same. Keith said "red"; flagged.
  - Cut Jason out of `jason-seated.jpg` locally with macOS Vision subject lifting (Swift script in the session scratchpad). Edges checked: clean. Saved as `site/img/jason-seated-cutout.webp` (900×1350, ~100KB, transparent). Original jpg kept.
  - Layout: `.hero-inner` align-items stretch; `.hero-photo` 520px column with the circle as a radial-gradient fill; Jason sits on the hero's bottom edge. Copy bottom padding 88→56px. At 1440 his head top is 210px vs headline top 198px (it was ~430px before).
  - Checked at 1440, 1280, 1100, 810 and 390: "Full Presence" stays on one line, no horizontal scroll; on tablet/phone Jason + circle sit below the copy.
- Step 3 (Keith's screenshots): centre the hero, and make the eyebrow lower case.
  - Eyebrow "For poker players who play for more than the money" now shows in sentence case (no uppercase transform, hero only), centred.
  - Everything in the hero copy column is centred (eyebrow, headline, rule, hint, button). The orange rule is shortened to 360px.
  - The hint block is now **one sentence at one size** (24px desktop, 20px phone): "Here's A Hint: Optimizing Your Routine … "Strong Mindset" Has NOTHING To Do With Elite Poker Performance". Same words; the all-caps line "HAS NOTHING TO DO WITH" is set in title case with NOTHING kept in caps and underlined orange. "Here's A Hint:" stays orange, "Elite Poker Performance" bold.
  - Follow-up: Keith asked for the hint at 18px. Now 18px at all widths (the 20px phone override was removed). The page uses px throughout.
  - Removed with the merge: the left orange border on the hint, the doodle underline under "Here's A Hint:" (can't sit under inline text), the separate small-caps "Has nothing to do with" line, and the 50px "Elite Poker Performance" line.

- Step 4 (Keith's screenshot of a press-logo bar straddling two sections): a **testimonial card that sits half in the hero, half in the letter** (requested by Keith).
  - Content: Ryan Hoenig snippet, verbatim first sentence of his testimonial ("Within months of joining Jason's program, I won my first WSOP bracelet and final tabled the next event I played."), 5 orange stars, name, and his first credential "WSOP Dealer's Choice Champion".
  - Circular photo: new `site/img/ryan-avatar.jpg`, a 240×240 square crop of Ryan's face from `ryan.jpg` (pre-cropped so the circle imports cleanly into Framer), 88px with an orange ring.
  - White card, 8px radius, big soft shadow, max 1000px. Built as `<figure class="hero-proof" data-framer-name="Hero Testimonial">` inside the Hero section, with `margin-bottom:-72px` (phone `-154px`, card stacks centred) and the Letter section given `.after-proof` padding to match (168px desktop / 210px phone).
  - Measured: exactly half above / half below the edge at 1440, 1100, 810 and 390. Between 641 and ~700px it's slightly uneven (card height varies); in Framer set the overlap per breakpoint by hand.
  - Framer note: negative margin overlap may not survive import; if not, place the card as its own layer across the boundary.

- FAQ restyled as accordion drop-downs (Keith's screenshot): mist `#EBF0F2` background; heading left-aligned with an orange 4px line running to the right; each question a white card with a 5px orange left border, 8px radius, orange SVG plus (turns to minus when open), navy question 22px; answer indented under the question.
  - Built with native `<details>/<summary>`: still **no JavaScript**. This overrides the old "FAQ is static, not an accordion" rule, at Keith's request. In Framer, rebuild with Framer's own Accordion component (details/summary won't import as interactive).
  - FAQ wording checked identical to before. No horizontal scroll at 1440 or 390.

- Bonuses restyled to match Keith's Russell Brunson screenshot ("FREE BONUS #1" card with tablet mockup and dashed price pill), in Jason's fonts/colours:
  - Each bonus is a white card (16px radius, deep shadow) on the navy section: iPad mockup left (260px; 200px tablet; stacked on top on phone), copy right.
  - Copy column: "BONUS #N" label (orange-deep caps), title (navy, 34px), bullets in body grey, then a dashed orange pill on a light orange tint (`#FFF0EB`): cloud-download icon + "Instant Access" on the left; the original value line struck through + **"Today: FREE!"** on the right. Bonus 7 keeps its orange outline as the featured one.
  - New microcopy (flag to Keith): "Instant Access" and "Today: FREE!" in each pill; label changed from "BONUS 1" to "Bonus #1". Didn't add the word "FREE" to the label. All original bonus wording unchanged (text diff checked).
  - Placeholder iPads: 7 hand-built SVGs in `site/img/bonus/bonus-1..7.svg` (generator script in the session scratchpad, `ipads.py`): royal flush in a spotlight, trophy + chip stacks, shield with spade, calm waves + face-down cards, video library grid, video-call coaching grid, checklist clipboard + chip. Each shows "BONUS #N" + the bonus name on screen. No image service used. Swap for real mockups later (keep `filter: drop-shadow`).
  - Container widened 900→1040px. Checked at 1440, 810, 390; no horizontal scroll.

- "Inside PR2, You Will Learn:" restyled like Keith's DotComSecrets screenshot: Jason's book cover **Poker With Presence: Unlocking The Final 15%** (Keith supplied it; saved as `site/img/poker-with-presence-cover.jpg`, 648×900, ~156KB) in the centre with a deep shadow, 3 learning points in white boxes on each side (1–3 left, 4–6 right, orange triangle bullets). Section background now mist `#EBF0F2` like the screenshot; Felipe's testimonial section below also switched to mist so there's no seam (it uses padding-top:0).
  - The DCS boxes have their own headings and handwritten notes ("The Fast Way To…"); not added, since we have no approved copy for them. Ask Keith if wanted.
  - Tablet/phone: book on top (300px / 240px), then the 6 boxes stacked in order.
  - Page text identical to before (checked). No horizontal scroll at 1440/810/390.

- Letter opening: Jason's photo added beside "Dear Friend", like Russell Brunson's "From: Russell Brunson" letter block, but **mirrored (photo left, text right)** as Keith asked.
  - Keith supplied a new studio shot (Jason, arms crossed on a table, black background). Cropped locally to portrait 4:5 and saved as `site/img/jason-arms-crossed.jpg` (800×1000, ~131KB). He looks to the right, towards the text.
  - Layout: `.letter-intro` (max 1120px, flex row, gap 64px): 440px photo with 16px radius + deep shadow, then "Dear Friend," … "This letter can show you how it's done." in the right column. The chevrons and the rest of the letter continue in the normal 700px centred column.
  - Tablet/phone: photo on top (max 420px), text below.
  - RB's photo has a trophy badge over the corner; not added (nothing equivalent supplied). Page text identical (checked).

- Keith asked for the letter-opening text to **wrap around** Jason's photo. Done with `float:left` on `.intro-photo` (400px desktop, 320px tablet; no float on phone, photo on top) inside a 980px `display:flow-root` block; paragraphs get 22px bottom margin there.
  - **Breaks the flexbox-only Framer rule** (exception approved by asking): Framer has no text wrap, so on import this block lands as photo + text side by side, or rebuild it there as two columns. Flagged to Keith.
  - Text under the photo runs 980px wide, wider than the 700px letter column that follows.

- Keith then asked to put the excess text in a separate block instead of wrapping. Float removed (back to flexbox only; the Framer exception in CLAUDE.md removed). Photo (440px) + "Dear Friend" … "satisfaction that money can't buy." side by side, vertically centred; then "And it's about the peace." … "This letter can show you how it's done." in the normal 700px letter column below, 64px gap. Phone/tablet: photo on top.

- Keith asked to restyle the "Full Presence Is a Skill … And It Can Be Trained" proof cards (screenshots: DotComSecrets box shadow, Tony Robbins card with handwritten note + arrow).
  - Cards are now **white** (16px radius) with a 3D look: an 8px light-grey slab edge under each card, a deep soft shadow, and a separate in-flow shadow strip below (`.case-shadow`, radial-gradient fill, so it imports to Framer).
  - **Removed the small labels** above each headline ("10 years stuck under $50k", "Scraping by at mid-stakes", "Tried every other program"). These were our microcopy, not Jason's.
  - Headlines ($1,000,000 / 10x Stakes / Months → Minutes) are now **handwritten** in Gochi Hand (Google Font, added for this only), orange-deep `#D62B00`, tilted -4°, with a hand-drawn SVG arrow curving down into the story. "Months → Minutes" sits on two lines so the three cards stay side by side on desktop.
  - Story text now dark on white (#444, bold in navy). Copy unchanged (checked).

- Keith asked to put the handwritten headlines and doodle arrows **outside the boxes, in white**. Moved each `.hand-row` above its card (still inside `.case-wrap`), text and arrows now `#FFFFFF` on navy, arrows point down into the card. "Months → Minutes" back on one line (36px desktop, 30px below 1240px) so all three cards line up. Checked at 1440/1100/1001/810/390, no overflow.

- Keith (screenshot) asked to rotate the 1st handwritten headline + arrow more steeply, and the 3rd the opposite way. `.tilt-l` rotates the whole row -13° (pivot bottom-left, about -17° with the text's own tilt), `.tilt-r` rotates +9° (pivot bottom-right, text +4°, so about +13°). The middle one stays at -4°. Transforms only, so the cards still line up; on phone the two tilted rows get 28px more space above. Checked at 1440/1100/810/390, no overflow.

- Keith supplied 6 stock poker photos and asked to use them in the bonus iPads. Cropped each locally with `sips` to the iPad screen shape (portrait, ~540×760, JPEG q62) and embedded them as base64 inside the existing `img/bonus/bonus-N.svg` frames (nothing uploaded; script `scratchpad/ipads_photo.py`). Mapping: 1 It Factor = ace of spades close-up; 2 Crushing The Series = casino table/dealer; 3 Unbreakable = grey royal-flush fan; 4 Conquer Cravings = chips + jack on white; 5 The Vault = J/Q/K spades close-up; 6 Group Coaching = hearts on dark wood; 7 Performance Plans = **reuses the casino photo**, cropped tight on the chips (6 photos for 7 bonuses, flagged). Kept the "BONUS #N" + title label on each screen, with a darker fade behind it so it reads on the light photos. SVGs are now 47–119KB each (~550KB total).

- Keith (One Comma Club screenshot) asked for a devices mockup in the "Everything you get" box: monitor, laptop, iPad and phone, using the bonus photos, sitting inside the box but sticking out the top. Built `site/img/stack-devices.svg` (1600×700, photos embedded as base64, ~330KB; script `scratchpad/devices.py`): monitor centre with "PR2 / Presence and Profit 2.0" over the hearts photo (navy fade + orange glow), laptop left (casino table), iPad right (ace of spades), phone front-right (chips + jack). Replaces the grey "PR2 product mockup goes here" slot. The box got `margin-top:120px` and the image `margin-top:-130px`, so it overhangs the top border; it is 112% of the box width on desktop (wider than the box, as in the screenshot) and 100% on tablet/phone (phone overhang 60px). `overflow:hidden` removed from `.stack`; the navy total bar got its own bottom radius. Soft `filter:drop-shadow` under the devices. Monitor text uses Helvetica/Arial (fonts can't load inside an `<img>` SVG). Checked 1440/1100/810/390, no overflow. Still a placeholder until the real PR2 mockup arrives.

- Keith asked to invert the "Everything you get" box: box now navy `#001E3A` (item names and values white, "Bonus N" labels orange `#FF3500`, row dividers `#24425F`, tick circles white with orange-deep `#D62B00` ticks); the "Total bonus value" bar is now white (label navy, $11,391 orange-deep `#D62B00`). Checked desktop and phone.

- Keith: the inverted stack "doesn't really work well", so reverse it. Restored `site/index.html` from c724ebd (white box, navy total bar, original tick colours). CLAUDE.md note removed.

- Keith (RB screenshot) asked for the stack ticks to become green rounded-square checkboxes and the values to show as "FREE!" with the value underneath, in the screenshot's colours. Ticks: white check on green `#12B312`, 5px radius. Values: "FREE!" 24px/900 green `#12B312` over "($1,500 Value)" 16px red `#E31B3D`, in a fixed 128px column (100px phone) so they line up. **New colours (green, red) and microcopy ("FREE!", "($X Value)") outside Jason's brand, both at Keith's request; flagged.** PR2 row has no value, unchanged. Total bar unchanged.

- Keith (One Comma Club screenshot) asked for the CTA button in that style at ~650px. Applied to the Offer CTA under the value stack only ("Yes, I Want In"), as `.btn.btn-green`: 650px max, green gradient `#16E01F`→`#0A9A0A`, 8px radius, 32px/800 white title with a dark-green `#0A8A0A` arrow beside it, subline 19px/400 white at 72% opacity, now in title case ("Instant, Lifetime Access To PR2", our microcopy, was all caps). The doodle arrows either side still fit (650 + 2×96 + gaps inside the 900px column). Phone: full width, 24px title. Other CTAs (hero, Inside PR2, sign-off, FAQ) still orange; offered to roll out.

- Keith asked to change ALL buttons to the green style. All 5 CTAs now `.btn.btn-green` (hero, Inside PR2, Offer, sign-off, FAQ). Arrow now sits inline after the last word (so it follows wrapped text); the two long "Join Now And Receive Instant, Lifetime Access To PR2" buttons get class `long` (25px title, balanced wrap, 2 lines). No sublines added to the others (would be new copy); only the Offer button has one. Hero button is 560px (limited by the hero copy column); others 650px. Phone: full width, 22px titles. Checked 1440 and 390, no overflow. The old orange `.btn` base style is still in the CSS underneath.

- Keith asked to put "PR2" and "Presence and Profit 2.0" on the same line, both red, subtitle in normal case. New `.product-line` flex row (baseline-aligned, centred): PR2 120px/900 + "Presence and Profit 2.0" 46px/800, both orange `#FF3500`, no caps/letter-spacing. Phone: 54px + 20px so it stays on one line. Copy has "PR2 (Presence and Profit 2.0)" with brackets; brackets still not shown (as before), mentioned to Keith.

- Keith asked for PR2 and "Presence and Profit 2.0" at the same size. Both now 68px/900 orange (52px tablet, 26px phone), 18px gap, one line at every width checked (1440/810/390).

- Keith (screenshot) asked to enlarge the Introducing PR2 tagline lines and make "Introducing …" italic, and to delete the doodle underline from all headlines. "Introducing …" now 38px/700 italic (Gabarito has no italic, so the browser slants it; same in Framer). Tagline: 44px/700 "The Coaching Program That Has Made", 56px/900 orange "A Whole Bunch Of Money", 44px "And Filled Many Trophy Cases", 34px "For A Whole Lot Of People" (tablet 34/44/27, phone 24/28/20). Removed all 8 doodle underline SVGs and their CSS (labels keep their `doodle-wrap` wrappers, harmless). Doodle arrows, chevrons and the proof-card handwriting arrows kept. Checked 1440/810/390, no overflow.

- Keith asked to put the Ryan Hoenig testimonial on a white background, remove the stars and recolour the text; same for Kevin Rabichow only (Felipe unchanged). Added `.testi-white` to both: white card, light border `#D6DEE3`, deep shadow, quote and name navy `#001E3A`, credentials grey-blue `#5A6B7A`. Stars removed from both (Felipe keeps his). Checked 1440 and 390.

- Keith asked to break the Bonuses heading into three lines via spans: "When You Join PR2," / "You Will Also Receive Instant Access" / "To The Following Bonus Trainings:". `h2.h2-lines` is a centred flex column of three spans (spaces kept between spans so the text reads the same). Desktop shows exactly those 3 lines; on phone the longer lines wrap within themselves. Wording unchanged.

- Keith (screenshot) asked to delete the "Included free" eyebrow above the Bonuses heading and size the heading like his screenshot. Eyebrow removed (it was our microcopy). Heading: line 1 "When You Join PR2," 72px/900, lines 2–3 44px/900 (tablet 56/34, phone 34/20, so each line stays on one line on phone). Checked 1440/810/390.

- Keith asked to delete the red stars from the Felipe Boianovsky testimonial. Removed (and the now-unused `.stars` CSS). No testimonial section has stars now; the small hero testimonial card still has its 5 stars.

- Keith asked to make the "The only place I am able to offer …" paragraph (Offer section, after "Outside of this program …") a headline, broken into his 5 lines. Now `h3.outside-h`: 5 spans, 32px/800 navy, centred (tablet 26px, phone 21px). Lines don't wrap above 1100px (the long 2nd line is ~943px, slightly wider than the 900px column, centred, no page overflow); below that, long lines wrap within themselves. Wording unchanged.

**Next**
- Continue hero refinement towards the Magnetic Marketing layout (Keith to direct the next step). Then price/checkout and the PR2 mockup. Then price/checkout. Still to get: PR2 product logo/mockup (Draft 2), plus the price and checkout platform.
