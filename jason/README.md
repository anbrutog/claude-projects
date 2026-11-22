# PR2 Sales Page (Jason Su)

Long-form sales page for PR2, built as static HTML and headed for Jason's Framer account.

- **Preview:** `cd site && python3 -m http.server 8000` → http://localhost:8000
- **Context for Claude Code / Antigravity:** see `CLAUDE.md` (decisions, design tokens, Framer-import rules, open items)
- **Copy:** `copy/PR2_copy.md` (locked wording), with issues for later in `copy/COPY-ISSUES.md`

## Suggested first prompt in Claude Code
> Read CLAUDE.md. Then [apply Jason's brand assets in /brand | wire the checkout links | prep the page for Framer import]. Keep the copy unchanged and keep the layout Framer-importable.

## Getting it into Framer (at the end)
1. Run the page locally or host it anywhere.
2. Install Framer's **HTML to Framer** Chrome extension. Copy one section at a time (each `<section>` is named) and paste into Jason's Framer project.
3. Narrow the browser to ~390px and repeat for the phone breakpoint.
4. In Framer: set button links, add animations, check breakpoints.
5. Alternative: the **Vortex – "AI Design to Framer"** plugin, which takes pasted HTML.

Test both import tools on the hero section in a scratch Framer project before touching Jason's.
