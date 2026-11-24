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

- Keith (screenshot) asked for the "only place I am able to offer" headline with varied line sizes. Each span now has its own size, measured to match his screenshot's proportions (widest line fills the 900px column), weight 900: desktop 52/30/46/52/39px, tablet 40/23/35/40/30, phone 22/16/18/20/18 (each line on one line except the long 2nd line, which wraps in two). Checked 1440/1100/810/390, no overflow.

- Keith asked for a nice hover on the CTA buttons. All `.btn-green`: 0.2s ease lift 3px, slightly brighter green, deeper green shadow, arrow slides 6px right; pressed state settles to 1px; keyboard focus gets the same effect plus a white outline; turned off under `prefers-reduced-motion`. First motion in the code (the no-animation rule is relaxed for this, at Keith's request). Framer import won't carry hover: rebuild as a Hover variant on the button component.

- Keith asked to delete the "Product mockup / VSL goes here" placeholder box in Introducing PR2. Removed (and its `.mock` CSS). If a VSL or mockup arrives later it needs a new slot.

- Keith asked for the same subtle hover movement (movement only) on the three proof cards and the bonus cards. `.case` and `.bonus` now lift 3px over 0.2s on hover (no colour/shadow change); off under `prefers-reduced-motion`. The proof cards' shadow strip stays put underneath. Rebuild as Hover variants in Framer.

- Keith asked for "It comes down to one thing only:" in lower case and the question laid out as "Do You Play With" / "Full Presence?". Label now sentence case, 20px/700 orange-deep (was 15px uppercase spaced); question split into two spans in a centred flex column. Same layout on desktop and phone.

- Keith asked to take out the dotted chevrons but keep them aside to maybe reuse in another section. Removed all 3 (end of opening letter, before "It comes down to one thing only", between the value stack and "Outside of this program"). Markup saved in `snippets/chevrons.html` (with where each one sat); the `.chevrons` CSS stays in the page so it can be dropped back in. Added 32px above "Outside of this program …" so it doesn't crowd the value box.

- Keith (RB "Get Your FREE Book, Send Me YOUR ADDRESS" screenshot) asked to restyle the Guarantee section like it, with "100 Day Guarantee" in place of "YOUR ADDRESS", a photo of Jason, and the box kept inside the navy glow section. New `.guar`: near-black box (`#131313`, 16px radius, deep shadow), copy left: orange "Try It For A Full 100 Days" (existing line) → white uppercase "100 DAY GUARANTEE" (64px/900, Keith's wording) → refund paragraph (unchanged) → "Jason Su" white Playfair signature → green CTA "Yes, I'm Ready To Start Now" (reused CTA copy, links #checkout). Photo right: new crop `img/jason-guarantee.jpg` (806×1000, from jason-table.jpg) fading into the box via CSS mask (Framer may not import the mask; use a gradient overlay there if needed). 100-day seal removed. Phone: photo on top fading down, copy centred. **Added a CTA button inside the guarantee (in the screenshot); flagged.**

- Keith asked to bring the FAQ question font weight down to 500. `.qa .q` 700 → 500 (answers unchanged).

- Keith (screenshot) asked to turn the Private coaching vs PR2 comparison into two side-by-side boxes: negatives with red X's on the left, positives with green ticks on the right. Built: left `.cmp.old` navy box (label + struck-through $25,000 + 4 red-X lines, white text); right `.cmp.new` mist box (label + $[PRICE] in orange-deep + 5 green-checkbox lines, navy text). 16px radius, stacked on phone. Replaced the old one-liners "Usually full." and "Plus over $10,000 worth of bonuses." (our microcopy).
  - **New list copy, needs Keith/Jason sign-off.** From Jason's copy: "Starts at $25,000 for six months of coaching", "My full attention and dedication … at a tiny fraction of the cost", "Instant, lifetime access to PR2", "Over $10,000 worth of bonuses", "Direct, personal feedback and coaching from me on anything you want help with", "100-day money back guarantee". **Written by us (factual claims Jason must confirm):** "Usually full, so you may have to wait for a spot", "Six months of coaching, then it ends", "Bonus trainings not included".

- Keith asked to remove the book cover from "Inside PR2, You Will Learn:" and make it a plain section: headline + bullets with the red arrow, white background. Section now `light` (white); the 6 points are a single centred `ul.learn-list` (max 780px, 20px text, orange triangle bullets, no boxes). Book cover and the DotComSecrets box layout removed (`poker-with-presence-cover.jpg` stays in `img/`, unused). Felipe's testimonial section switched back to `light` to match (it has no top padding, so it must share the background). "What's inside" eyebrow and CTA kept. Wording unchanged.

- Keith (DotComSecrets "Is This Book For Me?" screenshot) asked to style the Inside PR2 list box like it. `.learn-list` is now a white card: 1px `#E3E8EC` border, 20px radius, soft wide shadow, 56px/64px padding, max 1000px (tablet 44/40, phone 30/22, 16px radius). Ignored the smudge effect in the screenshot's corner, as asked.
- Fixed a thin navy line between two white sections (Inside PR2 → Felipe) on phone: the body background is navy and sub-pixel gaps between sections let it show. Added `.section+.section{margin-top:-1px}` site-wide.

- Keith (One Comma Club "What's My Investment?" screenshot) asked to raise the Inside PR2 box so it sits partly inside the section above, with the headline inside the box. New `.learn-card` (white, 1px border, 20px radius, soft shadow) holds the "What's inside" eyebrow, the h2 (52px), a divider (two grey lines + orange spade SVG, in place of the screenshot's logo; our decoration) and the list. Card is pulled up 180px (`margin-top:-180px`, z-index 2) into the Ryan testimonial section, which gets `padding-bottom:276px` (`.section.before-learn`) so the gap above the card stays ~95px; Inside PR2 section has no top padding. Phone: 90px overlap, 150px Ryan bottom padding, 30px headline. CTA stays below the card. Checked 1440/810/390.

- **Hero headline highlighter.** Keith asked for a yellow highlighter (from an "Attention:" screenshot) on "World Series And Triton Champions". Wrapped it in `<mark class="hl-yellow">`: pale yellow `#FFF9A6` with navy `#001E3A` text (white would be unreadable on yellow), and `box-decoration-break:clone` so it wraps cleanly on two lines. New name because `.hl` already exists on the page (orange text on navy). Yellow is a new colour; flagged to Keith. Checked at 1440/810/390, no overflow.

- **"Fuck it, I don't believe you" pull quote restyled.** Keith sent a quote-box screenshot (dashed border, light tint, quote mark icon, serif italic quote) and asked for the bonus "Instant Access" pill colours. Now `.pull` box: `#FFF0EB` fill, 2px dashed `#FF3500` border, 8px radius, inline SVG quote mark `#FFC3AE`, quote in **Merriweather italic 700** (new Google Font, closest match to the screenshot) navy, 44px desktop / 21px phone (one line). The screenshot's handwritten attribution was not added: the copy has none. Old orange top/bottom rules removed. Checked 1440/810/390, no overflow.

- **More Merriweather (Keith).** Added utility `.serif` (Merriweather italic 700) to: hero eyebrow "For poker players…" (now white), "Dear Friend,", "It comes down to one thing only:" (now navy `#001E3A`, was orange-deep), "The Good News Is …", "Introducing …", "Outside of this program …", "Try It For A Full 100 Days". Signatures `.sig` and `.guar-sig` switched from Playfair Display to Merriweather; Playfair removed from the font link. Testimonial quotes (`.hp-quote` hero card, `.testi-q` Ryan/Felipe/Kevin) now Merriweather italic **400** (lighter weight for longer text; names/credentials unchanged in Gabarito). Last stars removed (hero card `.hp-stars` + CSS). Font link now loads Merriweather ital 400+700. Checked 1440/390, no overflow.

- **"Outside of this program" headline weights (Keith).** Lines 2–5 now weight 500 by default; bold (900) only on "private coaching programs,", "which is usually full" and "$25,000 for six months of coaching." Orange `#FF3500` underline (4px, 3px on phone, no ink-skip) under "which is usually full" and "$25,000", same colour as the hero's NOTHING underline. Line 1 unchanged. Checked 1440/810/390, no overflow.

- **Comparison box headings (Keith).** Removed the struck-through "$25,000" and the "$[PRICE]" placeholder. Headings "Private coaching · 6 months" / "PR2 · Presence and Profit 2.0" now normal case, centred, 22px weight 700, same colour as each box's bullets (white on navy, navy on mist), with a 1px divider beneath (`#24425F` / `#D6DEE3`). Kept "2.0" (Keith typed "2"; flagged). Price now shown nowhere on the page. Checked 1440/390.

- **"Here's what it looks like:" in Merriweather (Keith).** Now `.serif` italic 700, sentence case, 24px, orange (was 14px uppercase Gabarito eyebrow). Checked 1440/390.

- **"As you can see …" in Merriweather (Keith).** Added `.serif` (italic 700), colour unchanged (muted light blue). Checked 1440.

- **Tinted heading bands (Keith, "Section #3: Funnel Scripts" screenshot).** New `.band` utility: full letter-column width, light orange `#FFF0EB` fill (same as the bonus pill, in place of the screenshot's pink), centred, no border/radius. Applied to "The Truth About Winning Big", the "It comes down to one thing only: / Do You Play With Full Presence?" block, "For the 99.9%, it's random." and "This is everything, literally.". Screenshot's bold-label/regular-rest mix applied where the line splits at a comma: **For the 99.9%,** it's random. / **This is everything,** literally. (our choice; flagged). Phone: lead-in 17px so "only:" doesn't wrap. Checked 1440/390, no overflow.

- **Bonuses heading weights (Keith).** Lines 2–3 ("You Will Also Receive … / To The Following Bonus Trainings:") now weight 500; "Instant Access" stays 900 with the orange `#FF3500` underline (4px, 3px phone), same style as the Outside-of-this-program headline. "When You Join PR2," unchanged. Checked 1440/390.

- **Good News lines (Keith).** "And It Can Be Trained" now white (was orange): "And It" weight 500, "Can Be Trained" 900 with orange `#FF3500` underline (5px desktop, 4px phone). "Here's what it looks like:" now muted blue `#ABC7D1` to match "The Good News Is …". Phone: both big lines 29px (were 38px and wrapping); each now fits on one line. Checked 1440/390, no overflow.

- **"As you can see …" bigger (Keith).** `.closer .seen`: 36px desktop (28px phone), font-family `"Merriweather",Georgia,serif` set explicitly (italic 700, muted blue, unchanged). Checked 1440/390.

- **Pull quote marks removed (Keith).** "Fuck it, I don't believe you" now without the curly quotes in the text; the SVG quote mark above it stays. Keith's explicit request (copy has the quotes).

- **"You tense up. / Freeze, overthink …" centred (Keith).** `.verbs` now centred. Checked 1440/390.

- **"Regardless of how big … / No matter how much pressure …" centred (Keith).** `.stack-lines` centred, orange left bar removed. Checked 1440/390.

- **Inside PR2 card trimmed (Keith).** Removed the "What's inside" eyebrow and the orange spade; the divider is now one plain grey line under the headline. Checked 1440/390.

- **Bonus bullets as green tick boxes (Keith screenshot).** All 14 bonus bullets: orange square `.dot` replaced by `.btick`, 20px rounded green box `#12B312` (same green as the value-stack and comparison ticks) with white tick SVG; slightly smaller than those (24–26px). Checked 1440/390, no overflow.

- **"Everything you get" box overlaps the Kevin section (Keith: "exact same" as Inside PR2).** Devices mockup removed from the page (`img/stack-devices.svg` file kept). `.stack` restyled like `.learn-card`: white, 1px `#E3E8EC` border, 20px radius (16px phone), same soft shadow, `margin-top:-180px` (-90px phone), z-index 2. Kevin section gets `before-stack` (padding-bottom 276px / 150px phone); Offer section `stack-sec` (padding-top 0). "Everything you get" label moved inside the box. Width stays 900px (the Offer column), vs 1100px for Inside PR2. Checked 1440/810/390, no overflow.

- **"Everything You Get" as a headline (Keith).** The small orange eyebrow in the value-stack card is now an `h2.h2.learn-h` (same as "Inside PR2, You Will Learn:": 52px / 40px tablet / 30px phone) with the same grey divider line beneath. Title-cased to match the headline format (our label, not Jason's copy). Checked 1440/810/390, no overflow.

- **All ticks restyled (Keith screenshot: plain bold tick, keep green).** Every tick on the page is now a plain bold green `#12B312` SVG tick (path `M3.5 13l5.5 5.5L21 5`, stroke 5.5, round caps), no box: 14 bonus bullets (`.btick` 20px), 8 value-stack rows (`.stick` 26px), 5 comparison ticks (`.cl-ico.tick` 24px), and the 5 "✓" text characters in the trust lines under CTAs (now `.tr-i` with a 14px SVG tick, stroke 5). Boxes' green backgrounds removed. Comparison red X's unchanged. Checked 1440/390, no overflow.

- **Hero orange circle removed (Keith).** Dropped the `radial-gradient` fill on `.hero-photo`; Jason's cut-out now sits straight on the navy hero glow. Checked 1440/390.

- **FAQ heading centred (Keith).** "Frequently Asked Questions" centred; the orange line beside it (`.faq-line`) removed with its CSS. Checked 1440/390.

- **"PR2 gets you … / At a tiny fraction … / My clients are paying me" resized (Keith screenshot).** Three sizes: 34/52/46px desktop (27/42/37 tablet, 15.5/26/24 phone); weights 800/900/500. "At a tiny fraction of the cost" is now navy with an orange `#FF3500` underline (5px, 3px phone) instead of orange text. Checked 1440/810/390, no overflow.

- **Bonuses "Total Bonus Value" as a headline (Keith).** Under the bonus cards: label now white, title case "Total Bonus Value", same size/weight as the "Everything You Get" headline (52px / 40px tablet / 30px phone, weight 800); "$11,391" stays orange `#FF3500` at the same size (weight 900). Wraps to two lines on phone. The navy total bar inside the value-stack card is unchanged. Checked 1440/810/390, no overflow.

- **CTA under the bonus total (Keith).** Added the green "Join Now And Receive Instant, Lifetime Access To PR2" button (copy of the Inside PR2 CTA, links to `#join`) with its three trust ticks, under "Total Bonus Value $11,391" in the Bonuses section. Checked 1440/390, no overflow.

- **Value-stack total bar matches the bonus total (Keith).** Navy bar at the bottom of the "Everything You Get" card now reads "Total Bonus Value $11,391" centred, white headline (52/40/30px, weight 800) with orange amount (900), replacing the small uppercase label left / amount right. Phone rule given `.stack .stack-total` specificity (the tablet block comes later in the CSS). Checked 1440/810/390, no overflow.

---

## 24 Nov 2026: Jason's version 2 copy

**Jason's email (via Keith)**
- Updated copy (pasted by Keith; saved as `copy/PR2_copy.md`, v1 in git history).
- Price reveal: move "Everything You Get" below the "Outside of this program" paragraph; extend its bottom with a struck-through $25,000 private coaching line, then "Your total investment: $1997 or 6 payments of $397"; then "As you can see … PR2 gets you my full attention and dedication".
- Mobile: hide the first (hero) photo of Jason.
- Copy the "Introducing The PR2 Formula" lines above the first green button in the hero, and keep them in the middle too.

**Decisions**
- Keith emailed Jason the plan and a **$100 extra charge** for this round (24 Nov).
- **Comparison boxes (private coaching vs PR2) will be removed** in the price-reveal step (Keith agreed; the struck-through $25k makes the same point).
- Order of work: 1) copy swap, 2) 100 → 60 days (waiting on Jason to confirm), 3) price reveal, 4) hide hero photo on phone, 5) compact "Introducing" block in hero.
- Open questions sent to Jason: 60-day guarantee everywhere? Wording "Private coaching (6 months): $25,000" for the struck-through line?

**Done: step 1, copy swap (wording only)**
- Hero headline: "Who You See On TV … To Show Them In".
- Letter opening rewritten. First 6 paragraphs sit beside the photo; from "killer instinct" on, in the column below. Short punch lines use `.oneline`.
- Truth About Winning Big rewritten; "I wish I'd gone for it" is its own bold line; routine parenthetical removed.
- Full Presence: "And no matter …"; the two "Can you still …" lines replaced by the "Will you be able to see that key detail …" paragraph; "Or worse …" and "The players at the top …" rewritten.
- "And It Can Be Trained." (full stop added, per copy).
- Introducing: "The PR2 Formula" (orange, 68/52/36px) with "(Presence and Profit 2.0)" as a smaller white line beneath (34/28/19px, weight 700). `.product-line` is now a column.
- Inside PR2: 7 new bullets (was 6). The pasted copy has no bold, so the old bold phrases are gone. Ask Keith for Jason's file if he wants bold carried over.
- Bonuses heading: "When you join PR2, / you will also unlock **over $10,000** / in bonus trainings and services:" (sentence case as written; the red underline moved from "Instant Access" to "over $10,000").
- Bonuses: #1 "Grow genuine…" removed, "Make yourself unreadable…" added; #2 bullet 1 rewritten (kept bold "largest lifetime score"); #4 "the" removed; #5 The Vault → **High Stakes Letters ($2000 value)**; #6 → **The Immersion ($2800)**; #7 → **6 Month Performance Lab Membership ($1997)** with 3 bullets (Custom Performance Plans removed; orange "feature" outline kept on #7). iPad SVG labels for 5–7 updated.
- Totals: **$10,794** (was $11,391) under the bonuses and in the value stack. Value-stack rows 5–7 updated; first row reads "The PR2 Formula (Presence and Profit 2.0)".
- Kevin: "Poker Strategy Coach to 100+ Professional Players".
- Close: added "More importantly … / It's the best and latest. / The exact ideas …"; "Nothing is held back." (underline kept).
- FAQ: Q2 answer extended; new Q3 "Other people sell programs for less money. Why should I buy yours?". **100-day wording left as is** until Jason confirms 60.
- `copy/COPY-ISSUES.md` rewritten for v2 (new typos: "show them in", "the was", "go come", "can't stop keep"; fixed items listed).
- Checked 1440/810/390, no overflow.

**Next**
- Continue hero refinement towards the Magnetic Marketing layout (Keith to direct the next step). Then price/checkout and the PR2 mockup. Then price/checkout. Still to get: PR2 product logo/mockup (Draft 2), plus the price and checkout platform.
