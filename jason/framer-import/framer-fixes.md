# PR2 page: Framer fixes (revision 2)

- **Page:** pokerwithpresence.com/pr2
- **Reference (how it should look):** https://pearldesign.ie/jason/
  - Resize the browser to see the tablet and phone versions.
- **Checked:** 26 Nov 2026, on the live page at desktop (1440px), tablet (810px) and phone (390px).

**Colours**

| Name | Hex |
|---|---|
| Navy | `#001E3A` |
| Navy-deep | `#00152A` |
| Orange | `#FF3500` |
| Orange-deep | `#D62B00` |
| Green tick | `#12B312` |
| Arrow green | `#0A8A0A` |
| Strike red | `#FF3B4E` |
| Body text | `#444444` |
| Muted | `#ABC7D1` |

**Fonts:** Gabarito for everything. Merriweather Italic for the serif lines.

---

## Done since the last check

- [x] "A Whole Bunch Of Money" is back in the PR2 Formula section.
- [x] All 7 green buttons link to `#join` (the Offer section). Fulfillment Policy links to `/fulfillment`.
- [x] Page title: "PR2 — Presence and Profit 2.0 | Jason Su".
- [x] Bold, italic and highlight inside paragraphs, apart from the 3 items in section 4.
- [x] "I wish I'd gone for it" is italic. "Nothing is held back." is underlined.
- [x] $25,000 in the value stack is struck through in red.
- [x] The "Yes, I Want In" subtitle is 72% white.
- [x] The bonus pill prices are 18px.
- [x] The ticks are green. The green buttons have their arrow.
- [x] The Hero and Guarantee glow backgrounds.

---

## 1. URGENT: the layout is broken on every screen size

The page is public. Anyone with the link can open it right now. Until this is fixed, either set the page back to **Draft** or don't share the link.

**What's wrong**
- The sections have been turned into vertical Stacks, which is right.
- But in 5 sections, the text and images inside are still set to **Position: Absolute**. That's left over from the HTML import.
- So they all sit at the top of the section on top of each other, and the section keeps its old fixed height. You get overlapping text, then a big empty gap.

| Section (Framer layer name) | Absolute layers inside | What you see |
|---|---|---|
| Letter Opening | 41 | Whole letter overlapped in one strip, then about 3,500px of blank white |
| Full Presence Results | 12 | Headline, proof cards and "As you can see…" piled on one line |
| Bonuses | 70 | Heading and the 7 bonus cards overlapping, then a long blank navy area |
| Offer and Pricing | 47 | "Outside of this program" lines and the value stack overlapping, then blank space |
| Closing Letter | 17 | Letter text overlapped, then blank space; the sign-off photo is half off-screen |
| Ryan, Felipe and Kevin Testimonials, Inside PR2, Guarantee | 1–3 each | The card floats over the section above it |
| Footer | 2 | The logo overlaps the © line |

**How to fix each section in Framer**
1. Select the section, then its content frame (for example "Letter Opening Desktop Content").
2. Select **all the layers inside it**: click the first, Shift-click the last.
3. In the right panel, under **Position**, change **Absolute** to **Relative**.
4. Set each layer's **Width** to **Fill** (text) or to a fixed size (images). Set **Height** to **Fit**.
5. Set the content frame's and the section's **Height** to **Fit**.
6. Check the layers are in reading order in the Layers panel, and drag any that aren't.
7. Repeat for any frames nested inside (cards, rows) that still show Absolute children.

**Do this on the Desktop breakpoint first.** Tablet and Phone inherit from Desktop, then you override them. At the moment Desktop has the phone layout on it: one column and full-width buttons.

---

## 2. Desktop layout (1200px and up)

Every section works the same way:
- The section is full width with its background colour, padding **96px** top and bottom and **24px** at the sides.
- Inside, a centred content frame has **Max Width** set, so the content doesn't stretch to the edges like it does now.

| Section | Content max width | Layout inside |
|---|---|---|
| **Hero** | 1120 | Logo bar: horizontal, space-between (logo left, "PR2 · PRESENCE AND PROFIT 2.0" right). Below it a **horizontal** row, gap 40: the copy column (Fill, centred text, gap 26) on the left and Jason's photo (**520px** wide, aligned to the bottom) on the right. |
| **Hero Testimonial card** | 1000 | **Horizontal**: round avatar 88px on the left, quote and name on the right, gap 28, padding 28/40. White, radius 8. It overlaps the bottom of the hero by 72px (negative margin or offset). |
| **Letter Opening** | 1120 for the top row, then **700** | Top row: horizontal, gap 64, Jason photo **440px** on the left, text column (max 620) on the right. Below it, a single 700px text column with gap 22. |
| **Full Presence Results** | 1120 | Headline block centred. **3 proof cards side by side**, gap 32, each Fill. Handwritten headline and arrow above each card. "As you can see…" block centred below. |
| **PR2 Formula** | 1120 | Centred column (already fine). |
| **Testimonials** (Ryan, Felipe, Kevin) | 1000 | **Horizontal**: photo **42%** on the left (fill height, cover crop), text on the right with padding 44 and gap 22. |
| **Inside PR2** | 1100 card | White card, radius 20, padding 64/72. It overlaps the bottom of the Ryan section by 180px. List max 900, gap 26. |
| **Bonuses** | 1120 | Heading centred. 7 bonus cards in a column, gap 28. Each card is **horizontal**: iPad image **260px** on the left, text on the right, gap 48, padding 40/48, radius 16. |
| **Offer and Pricing** | 900 for the value stack | "Outside of this program" lines centred, then the value stack card, then the "As you can see…" lines and the CTA with a doodle arrow either side. |
| **Closing Letter** | 700 | Single text column, gap 22. Sign-off row: photo 96px plus name, horizontal, gap 22. |
| **Guarantee** | 1100 | Black box, radius 16, **horizontal**: copy on the left (padding 56/0/56/64) and photo **400px** on the right with the left-edge fade. |
| **FAQ** | 880 | Heading, then the accordion items with gap 14 (already fine). |
| **Footer** | — | Centred column, gap 14: logo, link, ©. |

**Desktop text sizes** (these are currently 44–46px everywhere)

| Text | Size | Weight |
|---|---|---|
| “Full Presence” (hero) | 80px | 900 |
| Hero lead line | 28px | 700 |
| Hero closing line | 34px | 800 |
| "The PR2 Formula" (hero) | 40px | 900 |
| "Do You Play With / Full Presence?" | 52px | 900 |
| "Full Presence Is a Skill … / And It Can Be Trained." | 56px | 900 |
| "The PR2 Formula" (middle section) | 68px | 900 |
| "A Whole Bunch Of Money" (middle section) | 56px | 900, italic |
| "Inside PR2, You Will Learn:" and "Everything You Get" | 52px | 900 |
| "When you join PR2," | 72px | 900 |
| "you will also unlock" | 44px | **500** (now 400) |
| "Total Bonus Value $10,794" (both) | 52px | 800/900 |
| **$1,997** | 99px | 900 |
| "At a tiny fraction of the cost" | 52px | 900 |
| "60 DAY GUARANTEE" | 64px | 900 |
| Testimonial credentials and "($X Value)" in the stack | 16px | — (now 18) |

---

## 3. Tablet (810px): overrides

- Section padding: 96px top and bottom, 24px sides. The content frames keep their max width but are Fill.
- **Hero:**
  - Row becomes **vertical**, centred, gap 0.
  - Copy first, then the photo at **max 400px** wide.
  - "Full Presence" 62px.
- **Letter Opening:** top row **vertical**, centred, gap 40. Photo max 420px, text max 700px.
- **Full Presence Results:** proof cards wrap; 2 on the first row and 1 below is fine, or stack them vertically.
- **Testimonials:** **vertical**. Photo on top at **320px** high, cover crop.
- **Inside PR2:** card padding 48/40. Heading 40px.
- **Bonuses:** cards stay horizontal. Image 200px, gap 32, padding 32, title 28px.
- **Offer:**
  - "Outside" lines: 40 / 23 / 35 / 40 / 30px.
  - Stack total 40px.
- **Guarantee:**
  - Copy padding 44/0/44/40.
  - Heading 48px.
  - Photo 300px.

---

## 4. Phone (390px): overrides

- Section padding: **64px** top and bottom, **20px** sides. Body text 18px.
- **Hero:**
  - **Hide Jason's photo.**
  - Logo 26px high. Hide "PR2 · PRESENCE AND PROFIT 2.0".
  - Lead 20px, "Full Presence" 50px, closing line 24px. Orange rule max 220px.
  - "The PR2 Formula" 30px. Tagline 17px, "A Whole Bunch Of Money" 21px.
- **Hero Testimonial card:** **vertical**, centred text, gap 14, padding 24/20. Quote 18px.
- **Letter Opening:** photo full width above the text.
  - Pull quote 21px.
  - "Do You Play With Full Presence?" 38px.
  - Pink boxes: padding 20/18.
- **Full Presence Results:**
  - Cards **vertical**, full width.
  - "Full Presence Is a Skill…" 29px.
  - "It also works really damn fast." 28px.
- **PR2 Formula:** "The PR2 Formula" 36px, subtitle 19px, tagline 24px, "A Whole Bunch Of Money" 28px.
- **Testimonials:**
  - Photo 240px high.
  - Text padding 30/24.
  - Quote 20px.
- **Inside PR2:**
  - Card overlaps by 90px, padding 36/22, radius 16.
  - Heading 30px.
  - List text 17px, gap 20.
- **Bonuses:**
  - Each card **vertical**: image 200px centred on top, padding 28/20, gap 20.
  - Title 26px.
  - Pill: radius 16, text 16px.
- **Offer:**
  - "Outside" lines: 22 / 16 / 18 / 20 / 18px.
  - Value stack: header padding 28/18, rows padding 4/18.
  - Names 16px (PR2 row 18px), "BONUS N" 15px, value 20px. Value column 100px.
  - Total block 30px.
- **Closing Letter:** "This is everything" box padding 20/18.
- **Guarantee:**
  - **Vertical, photo on top** (300px high, fading out at the bottom: solid to 70%).
  - Copy centred, padding 8/22/36.
  - Small heading 20px, main heading 38px, body 17px.
- **FAQ:** question 19px, row padding 20/18.
- **Buttons:**
  - Title 22px, padding 22/18.
  - Arrow 28px wide, 10px gap.
  - The button width is Fill, but it **must not wrap the arrow onto its own line**.
- **Doodle arrows beside CTAs:** hide on Tablet and Phone. They're desktop only.

---

## 5. Still to fix (desktop and everywhere)

- [ ] **Hero hint underline.** The whole paragraph is underlined in orange. Only **"Here’s A Hint:"** and **"NOTHING"** should be underlined. Remove it from the rest.
- [ ] **"Outside of this program" block.** Every line is now 44px. Restore the sizes and weights:

  | Line | Size | Weight |
  |---|---|---|
  | "The only place I am able to offer" | 52px | 900 |
  | "this kind of long-term…" | 30px | 500 |
  | "is through my" (500) / **"private coaching program,"** (900) | 46px | as marked |
  | **"which is usually full"** (900, orange underline) / "and also starts" (500) | 52px | as marked |
  | "at" (500) / **"$25,000"** (900, orange underline) / **"for six months of coaching."** (900) | 39px | as marked |

- [ ] **Handwritten proof headlines are missing.** "$1,000,000", "10x Stakes" and "Months → Minutes" (Gochi Hand, 36px, white) were deleted from above the three proof cards. Add them back, each with its small white arrow.
- [ ] **Doodle arrows beside CTAs.** There should be 3 pairs (desktop only):
  - White either side of the Bonuses "Join Now" button.
  - Navy either side of "Yes, I Want In".
  - Navy either side of the FAQ "Yes, I'm Ready To Start Now".
  - Only 2 arrows are on the page now, and they're floating in the hero area.
- [ ] **Button arrow position.** Once the buttons have their proper width (max **650px**, centred), the arrow should sit **right after the text**, 16px gap, not pinned to the far right edge.
- [ ] **Guarantee photo fade.** After the layout fix, check the photo fades in from the left: a mask from transparent at the left edge to solid at 45%.
- [ ] **Hero Testimonial card.** It should overlap the hero/letter boundary, half in each. It currently sits below the hero.
- [ ] **Footer.** Logo, Fulfillment Policy and © should stack centred without overlapping. They're absolute now.

---

## Already matching (no action)

- All copy text
- Fonts
- Colours
- The FAQ accordion
- The glows
- Links
- The page title
- The ticks
