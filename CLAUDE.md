# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a collection of self-contained web projects served via XAMPP on localhost. Each project is a single HTML file (or a small directory) with no build step — open in a browser directly or via `http://localhost/sites/claude/`.

## Serving

XAMPP must be running (Apache). Files are accessible at:
```
http://localhost/sites/claude/<filename>.html
```

There is no build, compile, or install step. Edit the file and refresh the browser.

## Repository Conventions

- Each project is a **single self-contained HTML file** (HTML + CSS + JS in one file, no external dependencies).
- Commit messages follow Conventional Commits: `feat:`, `fix:`, `style:`, `refactor:`.
- Every change is committed and pushed to GitHub (`origin/main`).

## Git Workflow

```bash
git add <file>
git commit -m "feat: description"
git push
```

## Current Projects

| File | Description |
|------|-------------|
| `tictactoe.html` | Two-player Tic Tac Toe — dark UI, score tracking, win animations |

## Design Conventions (established)

- **Dark palette**: `--bg: #0f0f13`, `--surface: #1a1a24`, `--border: #2a2a38`
- **Accent colours**: X = `#7c6af7` (purple), O = `#f97a6a` (coral)
- **Typography**: `'Segoe UI', system-ui, -apple-system, sans-serif`
- **Radius**: cards `16px`, cells/inputs `12px`
- **No external dependencies** — no CDN links, no npm, pure vanilla JS
