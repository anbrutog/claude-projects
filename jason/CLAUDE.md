# PR2 Sales Page: project context

Read this first. It covers what this project is, what has been decided, and what is still open.

**Also read `SESSION-LOG.md`** for what happened in past sessions, and add to it as you go: each request, decision and change, newest session at the top.

## The job
- **Client:** Jason Su, a poker performance coach.
- **Product:** PR2 (Presence and Profit 2.0), an online coaching program for poker players.
- **Deliverable:** one long-form direct-response sales page.
- **Final platform:** Framer, in a **new project in Jason's Framer account**. Keith does not control that account, so we build and iterate the page as code here and import it into Framer at the end.
- **Deadline:** live before Black Friday. Keith wants it wrapped by the weekend of 22 Nov 2026.
- **Owner:** Keith (keithcommins.com / Best Sales Funnels), who builds it for Jason.

## Files
```
site/index.html      The page. One file, all CSS inline in <style>. No JS.
site/img/            Photos (already resized/compressed for the web)
  jason-seated-cutout.webp  hero (Jason cut out, transparent background, 900×1350, ~100KB)
  jason-seated.jpg   original hero portrait (black studio background), source for the cut-out
  jason-close.jpg    sign-off avatar
  poker-with-presence-cover.jpg  Jason's book cover (unused since 23 Nov)
  jason-arms-crossed.jpg  letter-opening photo (portrait crop of Keith's studio shot)
  jason-table.jpg    landscape shot, source for jason-guarantee.jpg
  jason-guarantee.jpg  portrait crop used in the Guarantee box
  ryan.jpg           Ryan Hoenig testimonial (Hard Rock trophy)
  felipe.jpg         Felipe Boianovsky testimonial (BSOP trophy)
  kevin.jpg          Kevin Rabichow testimonial (at the table)
copy/PR2_copy.md     Copy as markdown, version 2 from Jason (24 Nov); source of truth for wording
copy/PR2 v2.docx     Jason's version 2 copy file (24 Nov): source for bold/italic
copy/PR2_copy_original.docx   Original copy file from the client (v1)
copy/COPY-ISSUES.md  Typos/gaps to raise with Keith at the END, not now
snippets/chevrons.html  Dotted chevron divider, parked (Keith may reuse it)
```

Preview locally: `cd site && python3 -m http.server 8000` (or `npx serve site`).

## Hard rules
1. **Copy is locked.** Use Jason's wording exactly, typos included. Don't rewrite, trim or "improve" it. Known issues are logged in `copy/COPY-ISSUES.md` for Keith to raise at the end.
2. **Keep it Framer-importable.** The page will be pulled into Framer with Framer's **HTML to Framer** Chrome extension (copies static sections from a live page) or the **Vortex / "AI Design to Framer"** plugin (paste HTML). These tools only bring over static layout, so:
   - Layout uses **flexbox only**. Avoid CSS grid and avoid `::before`/`::after` decoration.
   - No JS-driven UI. The FAQ is an accordion built with native `<details>`/`<summary>` (no JS, Keith asked for it 22 Nov); rebuild it with Framer's Accordion component on import. No animations, except hovers Keith asked for on 22 Nov: CTA buttons (lift, brighten, arrow nudge) and proof/bonus cards (3px lift only). Rebuild them as Hover variants in Framer. Add other motion in Framer afterwards.
   - Images are real `<img>` tags, not CSS background images.
   - Fonts are **Google Fonts only** (Framer has them all).
   - Each top-level `<section>` has a `data-framer-name` so it can be imported one at a time and lands with a sensible layer name.
   - Inline SVG is used for the tick icons and the Russell Brunson-style doodles (underlines, arrows, dotted chevrons). They are in-flow flex children, not absolutely positioned, so they import as SVG layers.
3. **Responsive breakpoints match Framer's:** desktop (>1000px), tablet (≤1000px, Framer 810), phone (≤640px, Framer 390). For import, copy each section once at desktop width and once at ~390px for the phone breakpoint.

## Design system (Draft 2: Jason Su brand, taken from pokerwithpresence.com)
Matches Jason's site and coaching page (screenshots in `reference/`). Navy brand with orange accent; long reading sections on white.

| Token | Value | Use |
|---|---|---|
| Navy | `#001E3A` | brand dark: hero, dark bands, headings on light |
| Navy-deep | `#00152A` | alternate dark band (Introducing PR2), footer |
| Navy-card | `#062A4C` | cards on navy |
| Line | `#24425F` | borders on navy |
| Orange | `#FF3500` | ticks, big numbers, accents on navy |
| Orange-deep | `#D62B00` | orange *text* on light backgrounds (contrast) |
| Mist | `#EBF0F2` | light panels (learn list, value badges, old-price card) |
| Mist-2 | `#D6DEE3` | dividers on light |
| White | `#FFFFFF` | letter background |
| Body | `#444444` | body text on light |
| Muted-light | `#ABC7D1` | secondary text on navy |

- Font: **Gabarito** for everything (400–900; headings 800–900, tight letter-spacing). **Merriweather italic** (Keith, 23 Nov) for: "Jason Su" signatures, lead-in lines (`.serif`: Dear Friend, It comes down to…, The Good News Is…, Here's what it looks like:, As you can see…, Introducing…, Outside of this program…, Try It For A Full 100 Days) at 700, and testimonial quotes and credential lines (`.cred`, `.hp-cred`; names stay Gabarito, Keith 24 Nov) at 400. Playfair Display no longer used. **Gochi Hand** only for the handwritten proof-card headlines (Keith asked, 22 Nov). Merriweather also on the "Fuck it, I don't believe you" pull quote (dashed orange box).
- Radius: buttons **8px**, cards **8px**.
- **Buttons (Keith, 22 Nov):** all CTAs are green RB-style (`.btn-green`): gradient `#16E01F`→`#0A9A0A`, white 800 title + dark-green `#0A8A0A` arrow, max 650px. Replaces the orange buttons from his site.
- `.glow` sections (Hero, Full Presence proof, Guarantee) use navy with CSS radial gradients (orange glow bottom, blue glow top right), copying his hero. Gradients are fills, not images, so they import into Framer.
- His site's thin orange swoosh lines are **not** in the code. Add them in Framer as an SVG/image layer (decorative elements don't import reliably).
- Photos have black backgrounds, so they sit in black panels/cards on navy. Exception: the **hero** uses a transparent cut-out of Jason straight on the navy glow (the orange circle behind him was removed at Keith's request, 23 Nov). The photo column stretches to the copy's height and Jason sits on the hero's bottom edge. **Hidden on phone (≤640px)** at Jason's request (24 Nov): in Framer, hide that layer on the phone breakpoint.
- The cut-out was made locally with macOS Vision subject lifting (`VNGenerateForegroundInstanceMaskRequest`, a small Swift script) and converted to WebP in Chrome. No photo was uploaded anywhere. Repeat the same way for other photos.
- Logo: `site/img/brand/jason-su-logo-light.svg` (white text) in the hero bar and footer; `jason-su-logo-dark.svg` for light backgrounds.

## Page structure (section → `data-framer-name`)
1. Hero (copy column centred; eyebrow removed 24 Nov): tiered headline (small lead-in with "World Series And Triton Champions" in a yellow highlighter `.hl-yellow` `#FFF9A6`, Keith 23 Nov / huge "Full Presence" / medium close + orange rule), hint as one same-size sentence ("Here's A Hint: … Has NOTHING To Do With Elite Poker Performance"), compact "Introducing … / The PR2 Formula / (Presence and Profit 2.0)" as plain text (Jason, 24 Nov; tagline and box removed by Keith), CTA button (reuses "Join Now And Receive Instant, Lifetime Access To PR2"), Jason cut-out on the navy glow (orange circle removed 23 Nov), and a white testimonial card (Ryan snippet + round avatar `img/ryan-avatar.jpg`) straddling the hero/letter edge, half in each
2. Letter – Opening: Jason photo `img/jason-arms-crossed.jpg` on the left beside the first paragraphs (RB letter layout, mirrored), "Dear Friend" → "The Truth About Winning Big" → pull quote → "Do You Play With Full Presence?" → the .1%
3. Full Presence Can Be Trained: 3 white proof cards with 3D shadow (slab edge + `.case-shadow` strip), handwritten headlines ($1,000,000 / 10x Stakes / Months → Minutes) in white above each card, with white doodle arrows pointing into it
4. Introducing PR2: italic "Introducing …", "The PR2 Formula" (big, orange) over "(Presence and Profit 2.0)" (smaller, white) (v2 copy, 24 Nov), tagline lines 44/56/44/34px, tagline (mockup/VSL placeholder removed 22 Nov)
5. Testimonial – Ryan Hoenig (white card, no stars)
6. Inside PR2 (white): white card overlapping the bottom of the Ryan section (negative margin, like the hero testimonial card), holding headline + plain grey divider line (eyebrow and spade removed 23 Nov) + 7 learning points with orange triangle bullets (book cover removed 23 Nov) + CTA
7. Testimonial – Felipe Boianovsky (white section, to match Inside PR2)
8. Bonuses (v2 line-up, 24 Nov: It Factor, Crushing The Series, Unbreakable, Conquer Cravings, High Stakes Letters, The Immersion, 6 Month Performance Lab Membership): 7 white bonus cards (iPad SVG left in `img/bonus/bonus-N.svg`, with Keith's stock poker photos embedded as base64 on the screen (22 Nov); bonus 7 reuses the casino-table photo, cropped on the chips, "Bonus #N" label, title, bullets, dashed "Instant Access … Today: FREE!" pill) + "Total Bonus Value $10,794" (white headline, orange amount) + green Join Now CTA (Keith, 23 Nov)
9. Testimonial – Kevin Rabichow (white card, no stars)
10. Offer (price reveal, Jason's flow, 24 Nov): "Outside of this program …" headline → "Everything You Get" value stack card (standalone white card with shadow, no longer overlapping Kevin; plain bold green ticks `#12B312`; "FREE!" green over "($X Value)" red `#E31B3D`; PR2 + 7 bonuses) with an extended navy bottom: "Total Bonus Value $10,794" / "Private coaching (6 months): ~~$25,000~~" (our wording, red strike) / divider / "Your total investment:" / **$1,997** (big white) / "or 6 payments of $397" → "As you can see …" (serif, from Jason's email) → "PR2 gets you my full attention…" lines → green "Yes, I Want In" CTA with doodle arrows (`id="join"`). Comparison boxes removed 24 Nov (Keith).
11. Letter – Close: "This is everything, literally." → Jason Su sign-off + CTA
12. Guarantee: RB-style near-black box inside the navy glow section: "Try It For A Full 100 Days" / "100 DAY GUARANTEE" / refund text / Jason Su signature / green CTA, Jason photo right (`img/jason-guarantee.jpg`, CSS mask fade)
13. FAQ: 6 Q&As as accordion cards (details/summary, orange left border, plus icon) + CTA
14. Footer: Fulfillment Policy link, ©

### Design additions not in the copy (decided by us, flag to Keith if changing)
- Proof cards headline numbers: "$1,000,000", "10x Stakes", "Months → Minutes" (handwritten). The small labels above them were removed at Keith's request (22 Nov).
- "Total bonus value $10,794": the sum of the 7 listed bonus values (copy says "over $10,000").
- Guarantee section (reuses the refund-policy text from the FAQ). Heading "100 Day Guarantee" is Keith's wording (23 Nov); seal removed; CTA added there.
- Hero testimonial card straddling hero/letter (Keith asked for it, 22 Nov).
- Bonus card pills: "Instant Access" and "Today: FREE!" microcopy, original values struck through (Keith asked for the RB card style, 22 Nov). iPad images are placeholders.
- Trust lines under CTAs (✓ Instant access, ✓ Lifetime access, ✓ 100-day guarantee).
- Small eyebrow labels: none left ("Included free" removed 22 Nov; hero "For poker players who play for more than the money" removed 24 Nov).
- **Russell Brunson skill pass (22 Nov):** hand-drawn doodle underlines (**all removed at Keith's request, 22 Nov**), doodle arrows either side of the Offer CTA and the final FAQ CTA (desktop ≥900px only), 3 dotted-chevron dividers (removed 23 Nov; markup kept in `snippets/chevrons.html` for possible reuse). All in brand colours (orange `#FF3500` on navy, orange-deep `#D62B00` on white). The skill's own fonts/colours (Bebas Neue, Work Sans, red, gold buttons) were deliberately NOT used.
- **Offer value stack (approved by Keith, 22 Nov):** "Everything you get" box recapping the 7 bonus titles verbatim with values normalised to plain dollars ($497 … $2,800), total $10,794, plus a PR2 mockup slot. When the real mockup arrives, make it hover over the top of the box in Framer (skill pattern: overlap + drop-shadow).
- **Rule: don't add new sections or content blocks without asking Keith first.** The stack and the hero CTA were both approved explicitly.

## Open items / placeholders
- [x] **Price:** **$1,997 or 6 payments of $397** (Jason, 24 Nov), shown in the price reveal at the bottom of the "Everything You Get" card. Waiting on Jason to OK the "Private coaching (6 months): $25,000" wording.
- [ ] **Guarantee:** v2 copy says **60 days** (FAQ); page still says 100 everywhere until Jason confirms.
- [ ] **Checkout:** platform not decided (Stripe / ThriveCart / Kajabi?). All CTAs point at `#checkout` / `#join`.
- [ ] **PR2 logo + product mockup:** devices mockup in the value stack is a stand-in. The "Introducing PR2" VSL/mockup placeholder was removed (22 Nov); a VSL would need a new slot.
- [x] **Jason logo + brand colours/fonts:** pulled from pokerwithpresence.com and applied in Draft 2.
- [ ] **Fulfillment Policy page:** footer link has no target.
- [ ] Tracking: Keith said **no GA4**. Meta Pixel not discussed.
- [ ] Copy fixes: see `copy/COPY-ISSUES.md` (raise at the end).

## Status
- Draft 1 built and reviewed at desktop + phone widths (22 Nov 2026).
- Draft 2 (Jason's brand) applied and checked at desktop + phone widths (22 Nov 2026). Draft 1 styles are in git history (commit a8cb7c1).
- Next: fill price/checkout and the PR2 mockup, then import to Framer section by section and add breakpoints, animations and the swoosh lines there.
