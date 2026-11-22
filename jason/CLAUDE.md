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
   - Inline SVG is used only for the tick icons.
3. **Responsive breakpoints match Framer's:** desktop (>1000px), tablet (≤1000px, Framer 810), phone (≤640px, Framer 390). For import, copy each section once at desktop width and once at ~390px for the phone breakpoint.

## Design system (current: provisional until Jason's brand assets arrive)
Jason's photos all have black studio backgrounds, so the page is dark and premium with a cream "letter" background for the long reading sections.

| Token | Value | Use |
|---|---|---|
| Ink | `#0B0B0C` | page dark / hero |
| Coal | `#111113` / `#151517` | dark bands / dark cards |
| Line | `#2A2A2D` | dark borders |
| Paper | `#F5F0E6` | letter background |
| Paper-2 | `#EDE5D6` | cards on paper |
| Text dark | `#1B1A17` | |
| Text light | `#ECE7DD` | |
| Muted | `#A39E94` | |
| Gold | `#C9A24A` | accent, buttons (bracelet gold) |
| Gold light | `#E2C57E` | highlights, value badges |
| Gold deep | `#8A6E2E` | gold text on paper |

Fonts: **Playfair Display** (headings), **Source Serif 4** (body, 20px desktop / 18px phone), **Inter** (labels, buttons).

**Pending from Keith:** Jason's logo, brand colours/fonts and reference links. When they arrive, swap the tokens above, replace the text logo placeholder in the hero bar (`.logo-ph`) and add a PR2 product logo.

## Page structure (section → `data-framer-name`)
1. Hero: headline, "Here's a hint", "Has NOTHING to do with Elite Poker Performance", Jason photo
2. Letter – Opening: "Dear Friend" → "The Truth About Winning Big" → pull quote → "Do You Play With Full Presence?" → the .1%
3. Full Presence Can Be Trained: 3 proof cards ($1,000,000 / 10x Stakes / Months → Minutes)
4. Introducing PR2: product name, tagline, **mockup/VSL placeholder box**
5. Testimonial – Ryan Hoenig
6. Inside PR2: 6 learning bullets + CTA
7. Testimonial – Felipe Boianovsky
8. Bonuses: 7 bonus cards + "Total bonus value $11,391"
9. Testimonial – Kevin Rabichow
10. Offer: $25,000 private coaching vs **$[PRICE]** comparison + CTA (`id="join"`)
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

## Open items / placeholders
- [ ] **Price:** `$[PRICE]` in the Offer section. Not decided yet.
- [ ] **Checkout:** platform not decided (Stripe / ThriveCart / Kajabi?). All CTAs point at `#checkout` / `#join`.
- [ ] **PR2 logo + product mockup / VSL:** placeholder box in "Introducing PR2".
- [ ] **Jason logo + brand colours/fonts:** Keith is sending these.
- [ ] **Fulfillment Policy page:** footer link has no target.
- [ ] Tracking: Keith said **no GA4**. Meta Pixel not discussed.
- [ ] Copy fixes: see `copy/COPY-ISSUES.md` (raise at the end).

## Status
- Draft 1 built and reviewed at desktop + phone widths (22 Nov 2026).
- Next: apply Jason's brand once assets arrive (Draft 2), fill price/checkout, then import to Framer section by section and add breakpoints/animations there.
