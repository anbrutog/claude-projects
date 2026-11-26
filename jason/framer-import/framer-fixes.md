# PR2 page: Framer fixes (revision 3)

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

- [x] **No more overlapping layers.** Every section now flows top to bottom, and nothing runs off the side at any width.
- [x] "Outside of this program" block: the sizes, weights and orange underlines are right.
- [x] "A Whole Bunch Of Money" (middle section) is italic.
- [x] Footer: the logo no longer overlaps the © line.
- [x] From before:
  - links
  - page title
  - inline bold, italic and highlights
  - $25,000 strike-through
  - green ticks
  - button arrows
  - glows
  - FAQ accordion

---

## 1. Fix first: wrong or missing on every screen size

- [ ] **Two "Join Now" buttons have blue text.** On the Inside PR2 button and the Bonuses button, the text is link-blue on green and hard to read. Set the text colour to **white `#FFFFFF`**, 800 weight, the same as the hero button.
- [ ] **The Hero Testimonial card is gone.** This is the white card with Ryan's round photo:
  - Quote: “Within months of joining Jason’s program, I won my first WSOP bracelet and final tabled the next event I played.”
  - Then "Ryan Hoenig" and "WSOP Dealer’s Choice Champion".
  - It should sit across the bottom edge of the hero, half on the navy and half on the white. Add it back.
- [ ] **"Can Be Trained." is in the wrong place.** It's at the bottom of the Full Presence section, after "On that note, I’ve got something I want to show you."
  - Move it up so the headline reads: "Full Presence Is a Skill … / And It **Can Be Trained.**"
  - On desktop, "And It" and "Can Be Trained." sit on one line.
- [ ] **The handwritten proof headlines are still missing.** Add back "$1,000,000", "10x Stakes" and "Months → Minutes", each above its proof card:
  - Gochi Hand, 36px, white.
  - Each with its small white curved arrow pointing into the card.
- [ ] **The letter photo is at the end of the letter.** Jason's arms-crossed photo should be at the **start**, beside "Dear Friend," and the first paragraphs. On phone and tablet it goes above "Dear Friend,".
- [ ] **The hero hint is still underlined all the way through.** Only **"Here’s A Hint:"** and **"NOTHING"** get the orange underline. Remove it from the rest of the paragraph, including "Elite Poker Performance".
- [ ] **Bonus cards are in the wrong order inside.**
  - It should be:

    ```
    Desktop:  [iPad image 260px] | BONUS #N
                                 | Title
                                 | ✓ bullet
                                 | ✓ bullet
                                 | [pill]
    Phone:    iPad image (200px, centred)
              BONUS #N / Title / ✓ bullets / [pill]
    ```

  - Right now it's label, title, pill, image, bullets. Move the **pill to the bottom** and the **image to the top** (or to the left on desktop).
- [ ] **The bonus pill is broken.** It has grown into a big oval with its contents stacked.
  - It should be **one row**, padding 14/24, full radius (999), and about 56px tall:

    ```
    ( ☁ Instant Access                Cost: $1500 per attendee  Today: FREE! )
    ```

  - Left: cloud icon + "Instant Access". Right: struck price (grey) + "**Today: FREE!**" (800).
  - Use Distribute: Space Between, Align: Center.
  - **On Phone only:** radius 16, text 16px, and it can wrap onto 2 lines.
- [ ] **Value stack rows are broken up.** Each row's tick, "BONUS N", name and "FREE!/(Value)" are stacked vertically, and each tick has dropped to the top of the next row.
  - Each row should be **one horizontal line**, gap 14, padding 14 top and bottom, with a 1px `#D6DEE3` line underneath:

    ```
    ✓   BONUS 1                         FREE!
        The “It Factor”                 ($1,500 Value)
    ```

    - Tick: 26px, green.
    - Middle (Fill): "BONUS N" (18px desktop and 15px phone, 800, letter-spaced, navy) over the name (18px, 400).
    - Right column (128px desktop, 100px phone): "FREE!" (24px, 900, green `#12B312`) over "($X Value)" (16px, 500, red `#E31B3D`).
  - The PR2 row is the same but has no "BONUS" label, and its name is 21px, 800.
  - **Move "6 Month Performance Lab Membership"** back into the Bonus 7 row. It's currently stranded under the price box.
- [ ] **Trust lines are split up.** Under the 3 "Join Now" buttons, the 3 ticks sit in a vertical column with the labels in a row below them.
  - Each tick belongs **beside** its label, all on one line, centred: ✓ Instant access · ✓ Lifetime access · ✓ 60-day guarantee.
  - Tick 14px, 6px gap, 18px between items, text 14px, weight 500.
  - Same under "Yes, I Want In" (✓ Secure checkout · ✓ 60-day money back guarantee). Those are currently left-aligned and far below the button. Centre them directly under the button.
- [ ] **The "Yes, I Want In" block is in the wrong order.** It should read top to bottom:

  ```
  As you can see …
  PR2 gets you my full attention and dedication …
  At a tiny fraction of the cost      ← move up (currently below the button)
  My clients are paying me
  [ Yes, I Want In ]                  ← doodle arrow either side (desktop)
  ✓ Secure checkout   ✓ 60-day money back guarantee
  ```

- [ ] **Sign-off photo.** In the Closing Letter, Jason's round photo is below the button.
  - It belongs **to the left of the "Jason Su" signature**: a horizontal row, gap 22, photo 96px with an orange 3px border.
  - The "Yes, I’m Ready To Start Now" button comes after that row.
- [ ] **Doodle arrows beside the CTAs are missing.** There should be 3 pairs, on desktop only:
  - White, either side of the Bonuses "Join Now" button.
  - Navy, either side of "Yes, I Want In".
  - Navy, either side of the FAQ "Yes, I’m Ready To Start Now".
  - Use a horizontal row: arrow (120px) | button | arrow, gap 14, centred. Hide the arrows on Tablet and Phone.
- [ ] **FAQ questions are cut off on phone** ("Why are you so confident y…"). Set the question text to **Width: Fill** so it wraps.
- [ ] **Footer order (minor):** Fulfillment Policy, then logo, then ©. Right now the logo is last.

---

## 2. Desktop layout (1200px and up)

Desktop currently shows the phone layout stretched across the full screen: one column, with text and buttons running edge to edge. Set these on the **Desktop** breakpoint.

**Width rule for every section:**
- The section is full width, with padding **96px** top and bottom and **24px** at the sides.
- Inside it, a content frame is centred with **Max Width** set (table below).
- Body text never runs wider than **700px**.
- Buttons are **max 650px** wide, centred. The arrow sits right after the text with a 16px gap, not at the far right.

| Section | Content max width | Layout |
|---|---|---|
| **Hero** | 1120 | Logo bar: horizontal, **space-between**. The "PR2 · PRESENCE AND PROFIT 2.0" label goes far right. Below it, a **horizontal row**, gap 40: the copy column on the left (Fill, centred, gap 26, including the button) and Jason's photo on the right (**520px**, aligned to the bottom of the hero). |
| **Hero Testimonial card** | 1000 | **Horizontal**: avatar 88px on the left, quote and name on the right, gap 28, padding 28/40, white, radius 8, overlapping the hero bottom by 72px. |
| **Letter Opening** | 1120 top row, then **700** | Top row: horizontal, gap 64. Photo **440px** on the left (radius 16). "Dear Friend," and the first paragraphs on the right (max 620). The rest of the letter is in a 700px column, gap 22. |
| **Full Presence Results** | 1120 | Headline centred. **3 proof cards side by side**, gap 32, each Fill, with its handwritten headline above. "As you can see…" block centred below. |
| **Testimonials** (Ryan, Felipe, Kevin) | 1000 | **Horizontal**: photo **42%** on the left (fill height, cover crop), text on the right (padding 44, gap 22). |
| **Inside PR2** | 1100 | White card, padding 64/72, overlapping the Ryan section by 180px. List max 900. Button and trust line centred below the card. |
| **Bonuses** | 1120 | Cards in a column, gap 28. Each card **horizontal**: iPad 260px on the left, text on the right, gap 48, padding 40/48, radius 16. |
| **Offer and Pricing** | 900 | "Outside" lines centred. Value stack card max 900. "Yes, I Want In" block centred. |
| **Closing Letter** | 700 | Text column, gap 22. Sign-off row. Button. |
| **Guarantee** | 1100 | Black box, **horizontal**: copy on the left (padding 56/0/56/64, left aligned) and photo **400px** on the right with the left-edge fade (transparent → solid at 45%). |
| **FAQ** | 880 | Heading, then the items with gap 14. Button max 650. |

**Desktop text sizes** (most headings are still at phone size)

| Text | Size | Weight |
|---|---|---|
| Hero lead line | 28px | 700 |
| “Full Presence” (hero) | **80px** | 900 |
| Hero closing line | 34px | 800 |
| "The PR2 Formula" (hero) | 40px | 900 |
| "Do You Play With / Full Presence?" | 52px | 900 |
| "Full Presence Is a Skill … / And It Can Be Trained." | **56px** | 900 ("And It" 500) |
| "The PR2 Formula" (middle) | 68px | 900 |
| "Inside PR2, You Will Learn:" and "Everything You Get" | 52px | 900 |
| "When you join PR2," | 72px | 900 |
| "Total Bonus Value $10,794" (both) | 52px | 800/900 |
| **$1,997** | **99px** | 900 |
| "At a tiny fraction of the cost" | 52px | 900 |
| "60 DAY GUARANTEE" | 64px | 900 |
| "Jason Su" signature (Closing Letter) | 42px | Merriweather 700 italic |

---

## 3. Tablet (810px): overrides

The tablet view is close; the hero is right. Only change these:

- **Hero:** photo max **400px** wide (it's about 500 now). "Full Presence" 62px.
- **Letter Opening:** photo at the top, max 420px, centred.
- **Full Presence Results:** proof cards stacked, or 2 + 1.
- **Testimonials:** vertical, photo **320px** high (cover crop), full card width.
- **Bonuses:** cards **horizontal** again (image 200px on the left, text on the right), gap 32, padding 32, title 28px.
- **Guarantee:**
  - Horizontal, photo 300px on the right.
  - Copy padding 44/0/44/40.
  - Heading 48px.
- **Offer:** "Outside" lines 40 / 23 / 35 / 40 / 30px. Stack total 40px.

---

## 4. Phone (390px): overrides

Phone is mostly right now. Apart from the section 1 items, check these:

- **Hero:** photo hidden ✓. "Full Presence" **50px** (it's about 30 now). Lead 20px, closing line 24px.
- **Hero Testimonial card:** vertical, centred, padding 24/20, quote 18px.
- **Full Presence Results:** "Full Presence Is a Skill …" 29px. "And It Can Be Trained." 29px.
- **Testimonials:** photo 240px high and **full card width** (it's a smaller square now). Quote 20px.
- **Bonuses:** image 200px centred on top. Pill as in section 1, phone version.
- **Value stack:** rows as in section 1, with a 100px value column.
- **Buttons:** title 22px. The arrow sits on the same line as the last word.
- **Guarantee:** photo on top ✓, 300px high with a bottom fade (solid to 70%). Copy **centred**: it's left-aligned now.

---

## Already matching (no action)

- All copy text
- Fonts
- Colours
- Glows
- Links
- Page title
- Inline bold, italic and highlights
- "Outside of this program" block
- Everything You Get header and price block
- FAQ accordion
- Footer content
