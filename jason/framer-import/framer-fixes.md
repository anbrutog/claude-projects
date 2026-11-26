# PR2 page: remaining Framer fixes

Page: pokerwithpresence.com/pr2 (Framer, Draft)
Reference (how it should look): https://pearldesign.ie/jason/
Checked 25 Nov 2026 at desktop width (1440px). Tick each item off as you go.

Colours used below:
- Navy `#001E3A`
- Orange `#FF3500`
- Green tick `#12B312`
- Arrow green `#0A8A0A`
- Strike red `#FF3B4E`

Fonts: Gabarito for everything, Merriweather Italic for the serif lines.

---

## A. Must fix before launch

- [ ] **1. Missing line in the "PR2 Formula" section.** This is the section after "On that note, I've got something I want to show you."
  - Between "The Coaching Program That Has Made" and "And Filled Many Trophy Cases", the line **"A Whole Bunch Of Money"** is invisible.
  - Make it Gabarito Black (900), orange `#FF3500`, italic, the same size as the other tagline lines or a step larger.
- [ ] **2. Button links.** There are 8 green buttons.
  - Only the hero button is a link, and it points to `pearldesign.ie/jason/#join`. That is wrong: it sends visitors to the preview site.
  - Until checkout is decided, link all 8 buttons to the **"Yes, I Want In"** button section on this page, using a scroll-to link.
  - Later, swap in the checkout URL.
- [ ] **3. Footer link.** Link "Fulfillment Policy" to the page `/fulfillment`.
- [ ] **4. Tablet (810) and Phone (390) breakpoints.** These are not set up yet.
  - On phone the hero headline breaks one letter per line, and the "Everything You Get" box runs off the right edge.
  - Per section, set the stacks to **Fill** width and switch horizontal stacks to **vertical**.
  - Hide the hero photo of Jason on Phone.
- [ ] **5. Page title.** In Page Settings, under SEO, set the title to **PR2 — Presence and Profit 2.0 | Jason Su**. It is currently "Jason Su".

---

## B. Bold, underline, italic and highlight inside text

Framer merged these paragraphs into plain text. Select the words listed and apply the style.

**Style key**
- **Bold navy** = weight 700, colour `#001E3A`.
- **Orange underline** = underline in `#FF3500`.
  - Thickness 3px and offset 5px on small text.
  - Thickness 4px and offset 7px on the big headline lines.
- **Pale highlight** = background `rgba(255,53,0,0.14)` behind the words, the same technique as the yellow highlight in the hero.

| # | Section | Words | Style |
|---|---|---|---|
| - [ ] 6 | Hero, hint line | "Here’s A Hint:" | Weight 800 + orange underline |
| - [ ] 7 | Hero, hint line | "NOTHING" | Weight 800 + orange underline |
| - [ ] 8 | Hero, hint line | "Elite Poker Performance" | Weight 800 |
| - [ ] 9 | Letter, "Full Presence" paragraph | "nobody could have done it better than you did" | Bold navy + pale highlight |
| - [ ] 10 | Letter, pink box | "For the 99.9%," | Weight 800 (the rest of the line stays 400) |
| - [ ] 11 | Letter | “I wish I’d gone for it” | Italic |
| - [ ] 12 | Proof card 1 | "smashed through that", "million dollar win" | Bold navy |
| - [ ] 13 | Proof card 2 | "our first conversation," | Bold navy |
| - [ ] 14 | Proof card 3 | "resolved in minutes." | Bold navy (keep the closing ” plain) |
| - [ ] 15 | Inside PR2, bullet 1 | "six and seven figure wins" | Italic |
| - [ ] 16 | Inside PR2, bullet 1 | "with way less effort" | Bold navy |
| - [ ] 17 | Inside PR2, bullet 3 | "“presence mind control” technique" | Bold navy |
| - [ ] 18 | Bonuses heading | "over $10,000" | Weight 900 + orange underline (4px) |
| - [ ] 19 | Bonuses heading | "in bonus trainings and services:" | Weight 500 (now 400) |
| - [ ] 20 | Bonus #2, bullet 1 | "largest lifetime score" | Bold navy |
| - [ ] 21 | Bonus #7, bullet 1 | "face-to-face coaching" | Bold navy |
| - [ ] 22 | Bonus #7, bullet 3 | "ask me any question you like" | Bold navy |
| - [ ] 23 | "Outside of this program" block | "this kind of long-term individual attention to solving your problems" | Weight 500 (now 400) |
| - [ ] 24 | same block | "private coaching program," | Weight 900 |
| - [ ] 25 | same block | "which is usually full" | Weight 900 + orange underline (4px) |
| - [ ] 26 | same block | "$25,000" | Weight 900 + orange underline (4px) |
| - [ ] 27 | same block | "for six months of coaching." | Weight 900 |
| - [ ] 28 | Close letter, pink box | "This is everything," | Weight 800 ("literally." stays 400) |
| - [ ] 29 | Close letter | "Nothing is held back." | Orange underline (3px) |
| - [ ] 30 | Close letter | "over $10,000 worth of bonuses" | Bold navy + pale highlight |

---

## C. Other text fixes

- [ ] **31. Value stack price line.** In "Private coaching (6 months): $25,000", the **"$25,000"** should be weight 800, white, with a **strikethrough in red `#FF3B4E`**. Right now it looks like part of the price.
- [ ] **32. "Yes, I Want In" button subtitle.** "Instant, Lifetime Access To PR2" should be white at **72% opacity**, weight 400.
- [ ] **33. Bonus card pills.** The struck-out prices ("Cost: $1500 per attendee", "Regular Price: $800" and so on, 7 cards) should be **18px**, not 16px. The strikethrough and grey `#8A8A8A` stay as they are.

---

## D. Icons

SVG files are in `framer-import/svg/`. Drag them into Framer, or copy the SVG code and paste it on the canvas.

- [ ] **34. Ticks should be green, not navy.** Use `tick-green.svg` (`#12B312`) in each of these:
  - Bonus card bullets: 7 cards, 2–3 ticks each, 20px.
  - The "Everything You Get" list: 8 rows, 26px.
  - The trust lines under the buttons ("Instant access · Lifetime access · 60-day guarantee"): 14px.
- [ ] **35. Button arrows.** Every green button should end with the small dark-green arrow `button-arrow.svg`:
  - 34×18px, colour `#0A8A0A`.
  - 16px gap after the button text.
  - 28px wide on Phone.
  - The buttons are: hero, Inside PR2, Bonuses, "Yes, I Want In", close letter, Guarantee, FAQ, plus any others.

---

## E. Backgrounds, photo and handwriting

- [ ] **36. Glow backgrounds** on the **Hero** and **Guarantee** sections, which are now flat navy. "Full Presence Can Be Trained" uses the same glow, so check it too. The fill is navy `#001E3A` with two radial gradients on top:
  - **Orange glow:** centre at the bottom middle (50% across, just below the bottom edge). Colour `#FF3500` at 38% opacity, fading to 0%. Size about 70% of the width and 55% of the height.
  - **Blue glow:** centre at the top-right corner. Colour `#0A4A8C` at 55% opacity, fading to 0%. Size about 45% × 45%.
- [ ] **37. Guarantee photo fade.** Jason's photo in the Guarantee box should fade in from the left, so there's no hard edge against the black box.
  - Add a mask that runs from transparent on the left edge to solid at 45% across.
  - On Phone, fade out at the bottom instead: solid to 70%, transparent at the bottom.
- [ ] **38. Proof card handwriting tilt (optional).** The white handwritten headlines above the three proof cards are tilted on the reference page:
  - "$1,000,000" with its arrow: rotate about **-17°**, pivoting from the bottom-left.
  - "10x Stakes": rotate **-4°**.
  - "Months → Minutes" with its arrow: rotate about **+13°**, pivoting from the bottom-right.

---

## Already matching (no action)

- All copy text
- Fonts
- Testimonials
- FAQ accordion
- "Everything You Get" layout and price block
- Doodle arrows beside the CTAs
- Photos
- Overall spacing at desktop
