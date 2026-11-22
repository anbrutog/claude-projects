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
  jason-seated.jpg   hero (portrait, black studio background)
  jason-close.jpg    sign-off avatar
  jason-table.jpg    spare landscape shot (unused so far)
  ryan.jpg           Ryan Hoenig testimonial (Hard Rock trophy)
  felipe.jpg         Felipe Boianovsky testimonial (BSOP trophy)
  kevin.jpg          Kevin Rabichow testimonial (at the table)
copy/PR2_copy.md     Copy as markdown (source of truth for wording)
copy/PR2_copy_original.docx   Original copy file from the client
copy/COPY-ISSUES.md  Typos/gaps to raise with Keith at the END, not now
```

Preview locally: `cd site && python3 -m http.server 8000` (or `npx serve site`).

## Hard rules
1. **Copy is locked.** Use Jason's wording exactly, typos included. Don't rewrite, trim or "improve" it. Known issues are logged in `copy/COPY-ISSUES.md` for Keith to raise at the end.
2. **Keep it Framer-importable.** The page will be pulled into Framer with Framer's **HTML to Framer** Chrome extension (copies static sections from a live page) or the **Vortex / "AI Design to Framer"** plugin (paste HTML). These tools only bring over static layout, so:
   - Layout uses **flexbox only**. Avoid CSS grid and avoid `::before`/`::after` decoration.
   - No JS-driven UI: FAQ is static, not an accordion. No animations. Add motion in Framer afterwards.
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
| Orange | `#FF3500` | buttons, ticks, big numbers, accents on navy |
| Orange-deep | `#D62B00` | orange *text* on light backgrounds (contrast) |
| Mist | `#EBF0F2` | light panels (learn list, value badges, old-price card) |
| Mist-2 | `#D6DEE3` | dividers on light |
| White | `#FFFFFF` | letter background |
| Body | `#444444` | body text on light |
| Muted-light | `#ABC7D1` | secondary text on navy |

- Font: **Gabarito** for everything (400–900; headings 800–900, tight letter-spacing). **Playfair Display italic** only for the "Jason Su" signature.
- Radius: buttons **3px** (as on his site), cards **8px**.
- `.glow` sections (Hero, Full Presence proof, Guarantee) use navy with CSS radial gradients (orange glow bottom, blue glow top right), copying his hero. Gradients are fills, not images, so they import into Framer.
- His site's thin orange swoosh lines are **not** in the code. Add them in Framer as an SVG/image layer (decorative elements don't import reliably).
- Photos have black backgrounds, so they sit in black panels/cards on navy.
- Logo: `site/img/brand/jason-su-logo-light.svg` (white text) in the hero bar and footer; `jason-su-logo-dark.svg` for light backgrounds.

## Page structure (section → `data-framer-name`)
1. Hero: headline, "Here's a hint", "Has NOTHING to do with Elite Poker Performance", CTA button (reuses "Join Now And Receive Instant, Lifetime Access To PR2"), Jason photo
2. Letter – Opening: "Dear Friend" → "The Truth About Winning Big" → pull quote → "Do You Play With Full Presence?" → the .1%
3. Full Presence Can Be Trained: 3 proof cards ($1,000,000 / 10x Stakes / Months → Minutes)
4. Introducing PR2: product name, tagline, **mockup/VSL placeholder box**
5. Testimonial – Ryan Hoenig
6. Inside PR2: 6 learning bullets + CTA
7. Testimonial – Felipe Boianovsky
8. Bonuses: 7 bonus cards + "Total bonus value $11,391"
9. Testimonial – Kevin Rabichow
10. Offer: $25,000 private coaching vs **$[PRICE]** comparison + CTA with doodle arrows (`id="join"`)
11. Letter – Close: "This is everything, literally." → Jason Su sign-off + CTA
12. Guarantee: 100-day seal
13. FAQ: 6 static Q&As + CTA
14. Footer: Fulfillment Policy link, ©

### Design additions not in the copy (decided by us, flag to Keith if changing)
- Proof cards headline numbers: "$1,000,000", "10x Stakes", "Months → Minutes", plus small labels above them.
- "Total bonus value $11,391": the sum of the 7 listed bonus values (copy says "over $10,000").
- 100-day guarantee seal section, which reuses the refund-policy text from the FAQ.
- Trust lines under CTAs (✓ Instant access, ✓ Lifetime access, ✓ 100-day guarantee).
- Small eyebrow labels ("For poker players who play for more than the money", "What's inside", "Included free").
- **Russell Brunson skill pass (22 Nov):** hand-drawn doodle underlines under 9 labels (never under headings), doodle arrows either side of the Offer CTA and the final FAQ CTA (desktop ≥900px only), 2 dotted-chevron dividers (end of opening letter, before "Do You Play With Full Presence?"). All in brand colours (orange `#FF3500` on navy, orange-deep `#D62B00` on white). The skill's own fonts/colours (Bebas Neue, Work Sans, red, gold buttons) were deliberately NOT used.
- **No new sections or content blocks.** Keith rejected an added offer-stack box (22 Nov): design passes may restyle and decorate existing content only, never add sections. Only exception so far: the hero CTA button, which Keith asked for.

## Open items / placeholders
- [ ] **Price:** `$[PRICE]` in the Offer section. Not decided yet.
- [ ] **Checkout:** platform not decided (Stripe / ThriveCart / Kajabi?). All CTAs point at `#checkout` / `#join`.
- [ ] **PR2 logo + product mockup / VSL:** placeholder box in "Introducing PR2".
- [x] **Jason logo + brand colours/fonts:** pulled from pokerwithpresence.com and applied in Draft 2.
- [ ] **Fulfillment Policy page:** footer link has no target.
- [ ] Tracking: Keith said **no GA4**. Meta Pixel not discussed.
- [ ] Copy fixes: see `copy/COPY-ISSUES.md` (raise at the end).

## Status
- Draft 1 built and reviewed at desktop + phone widths (22 Nov 2026).
- Draft 2 (Jason's brand) applied and checked at desktop + phone widths (22 Nov 2026). Draft 1 styles are in git history (commit a8cb7c1).
- Next: fill price/checkout and the PR2 mockup, then import to Framer section by section and add breakpoints, animations and the swoosh lines there.
