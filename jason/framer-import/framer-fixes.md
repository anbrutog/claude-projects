# PR2 page: Framer fixes (revision 4)

- **Page:** pokerwithpresence.com/pr2
- **Reference (how it should look):** https://pearldesign.ie/jason/
  - Resize the browser to see the tablet and phone versions.
- **Checked:** 27 Nov 2026, on the live page at desktop (1440px), tablet (810px) and phone (390px).
- Includes Jason's notes from his 27 Nov email.

**Summary**
- **Desktop is essentially done.**
- **Phone and tablet are the problem.** On phone:
  - Most headings have been set to one size, **32px**, whatever their original size was. Big headlines shrank and small lines grew, so lines break in different places.
  - Body text is **20px**. It should be **18px**.
  - This is what Jason means when he says the page "doesn't feel like much the same page".
- Fix the **phone** text sizes first (section 2), then the phone layout items (section 1), then tablet (section 3).

---

## 1. Phone (390px): missing or out of place

- [ ] **Inside PR2 list has no bullets** (Jason flagged this).
  - Each of the 7 points needs its small orange triangle (▸, `#FF3500`) on the left, with a 12px gap, as on desktop.
- [ ] **Handwritten proof headlines and arrows are gone** (Jason flagged this).
  - On desktop, "$1,000,000", "10x Stakes" and "Months → Minutes", with their white curly arrows, sit above the 3 proof cards. On phone they're hidden.
  - Show them on phone too: Gochi Hand, **30px**, white, one above each card.
- [ ] **"Can Be Trained." is on its own line**, under a lonely "And It".
  - Phone should read "And It **Can Be Trained.**" on one line, at 29px.
- [ ] **Hero: "PR2 · PRESENCE AND PROFIT 2.0" label shows** next to the logo and wraps onto 2 lines. Hide it on phone.
- [ ] **Hero: the hint is underlined all the way through.** Only "Here's A Hint:" and "NOTHING" get the orange underline. This is right on desktop but wrong on phone.
- [ ] **Hero testimonial card no longer overlaps the hero.** It sits below the navy. Pull it up so about half of it is on the navy, as on desktop.
- [ ] **Letter photo is at the end of the letter**, after "The players at the top…". On phone it belongs **above "Dear Friend,"**, full width.
- [ ] **"At a tiny fraction of the cost" is below the "Yes, I Want In" button.** This is right on desktop but wrong on phone.
  - Order: PR2 gets you… → At a tiny fraction of the cost → My clients are paying me → button → trust line.
- [ ] **Sign-off photo is below the button.** It should be beside the "Jason Su" signature, with the button after that row. This is right on desktop.
- [ ] **Value stack:** "Bonus 7" is in lower case. It should be "BONUS 7", like the others.
- [ ] **Tagline spacing (hero):** the 4 tagline lines have big gaps between them. Set gap **2px**.

> Note: some of these are right on desktop but wrong on phone. That usually means the phone breakpoint has its own override (a different layer order, a hidden layer or a text style). Reset those overrides on the Phone breakpoint so phone inherits from desktop again, then apply only the sizes below.

---

## 2. Phone (390px): text sizes

Body text everywhere: **18px**, line height 1.6 (it's 20 now). A dash in the "Live now" column means the size couldn't be measured; check it by eye.

| Text | Should be | Live now |
|---|---|---|
| **Hero** | | |
| "Why Do So Many Of The … Train Them In" | 20px, 700 | 28 |
| “Full Presence” | **50px**, 900 | 32 |
| "After Having Worked With The Other Top Coaches?" | 24px, 800 | 32 |
| Hint paragraph | 18px, 500 | 18 ✓ |
| "Introducing …" | 16px | 18 |
| "The PR2 Formula" | 30px, 900 | 32 |
| "(Presence and Profit 2.0)" | 15px, 700 | 17 |
| Tagline lines | 17px, 700 | 21 |
| "A Whole Bunch Of Money" | 21px, 900 | 27 |
| Button title | 22px, 800 | 18 |
| **Letter** | | |
| "The Truth About Winning Big" | 27px, 800 | 32 |
| "Fuck it, I don't believe you" | 21px, Merriweather 700 italic | 32 |
| "It comes down to one thing only:" | 17px | 20 |
| "Do You Play With Full Presence?" | 38px, 900 | — |
| "For the 99.9%, it's random." | 25px | 32 |
| **Full Presence section** | | |
| "Full Presence Is a Skill …" / "And It Can Be Trained." | 29px | 32 |
| "As you can see …" / "It also works really damn fast." | 28px | 32 |
| **Middle PR2 Formula section** | | |
| "The PR2 Formula" | 36px, 900 | — |
| "(Presence and Profit 2.0)" | 19px | — |
| Tagline lines / "A Whole Bunch Of Money" / last line | 24 / 28 / 20px | — |
| **Testimonials** | | |
| Quote | 20px | 24 |
| Credential lines | 16px | 18 |
| **Inside PR2** | | |
| "Inside PR2, You Will Learn:" | 30px | 32 |
| List items | 17px | 20 |
| **Bonuses** | | |
| "When you join PR2," | 34px, 900 | 32 |
| "you will also unlock over $10,000 / in bonus trainings and services:" | **20px** | 32 |
| Bonus title | 26px, 800 | 32 |
| Struck price in the pill | 16px | 12 |
| "Total Bonus Value $10,794" | 30px | 32 |
| **Offer** | | |
| "The only place I am able to offer" | 22px, 900 | 32 |
| "this kind of long-term individual attention…" | 16px, 500 | 32 |
| "is through my private coaching program," | 18px | 32 |
| "which is usually full and also starts" | 20px | 32 |
| "at $25,000 for six months of coaching." | 18px, 900 | 32 |
| Value stack row names | 18px (PR2 row 18px, 800) | 14 |
| "($X Value)" | 14px | 12 |
| "Private coaching (6 months): $25,000" | 15px | 26 |
| "Your total investment:" / "or 6 payments of $397" | 15px | 26 |
| **$1,997** | **57px**, 900 | 32 |
| "PR2 gets you my full attention and dedication …" | 16px, 800 | 32 |
| "At a tiny fraction of the cost" | 26px, 900 | 32 |
| "My clients are paying me" | 24px | 32 |
| "Yes, I Want In" / subline | 22 / 15px | 32 / 19 |
| **Closing** | | |
| "This is everything, literally." | 27px | 32 |
| "Jason Su" signature | 36px | 32 |
| "Yes, I'm Ready To Start Now" | 22px | 32 |
| **Guarantee** | | |
| "Try It For A Full 60 Days" | 20px | 28 |
| "60 DAY GUARANTEE" | 38px | 32 |
| Guarantee paragraph | 17px | 19 |
| **FAQ** | | |
| "Frequently Asked Questions" | 30px | 32 |
| Questions | 19px | 22 |

---

## 3. Tablet (810px): text sizes

The layout is fine. Only these sizes are off:

| Text | Should be | Live now |
|---|---|---|
| “Full Presence” (hero) | 62px | 46 |
| "Full Presence Is a Skill …" / "And It" | 56px | 46 |
| "Inside PR2, You Will Learn:" | 40px | 46 |
| "When you join PR2," | 56px | 44 |
| "you will also unlock … services:" | 34px | 44 |
| Struck price in bonus pills | 18px | 12 |
| "Total Bonus Value $10,794" | 40px | 46 |
| "Outside of this program" lines (5 lines, top to bottom) | 40 / 23 / 35 / 40 / 30px | all 44 |
| "Everything You Get" | 40px | 30 |
| Value stack: "BONUS N" / PR2 row name | 18 / 21px | 14 / 14 |
| "FREE!" / "($X Value)" | 24 / 16px | 20 / 12 |
| "Private coaching…" / "Your total investment:" / "or 6 payments…" | 20px | 26 |
| **$1,997** | **76px** | 32 |
| "PR2 gets you my full attention…" | 27px | 34 |
| "At a tiny fraction of the cost" / "My clients are paying me" | 42 / 37px | 46 / 46 |

---

## 4. Desktop (1440px)

Done. Everything matches, apart from one small thing:

- [ ] There's about 250px of empty white space between the hero testimonial card and the letter photo. Cut it to about 64px.

---

## Already matching (no action)

- All copy
- Fonts and colours
- Links and checkout
- Page title
- Glows
- Bonus card ticks
- FAQ accordion
- Footer
- The whole desktop layout
