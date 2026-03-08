# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Purpose

A collection of single-file, vanilla HTML/CSS/JS mini-projects and games. No build tools, no dependencies, no frameworks — every project is one `.html` file that runs directly in a browser.

## Running Projects

```bash
open <filename>.html          # macOS — opens in default browser
```

No build step, no install, no server required.

## Git Workflow

All changes must be committed and pushed to GitHub after every meaningful change:

```bash
git add <file>
git commit -m "descriptive message"
git push
```

- Remote: https://github.com/seemalz/agentic-project
- Default branch: `main`
- Always push after committing — the user relies on GitHub as the save/revert mechanism.

## Code Style & Architecture

All projects follow the same pattern established in `tictactoe.html`:

- **Single file**: all HTML, CSS, and JS in one `.html` file, in that order (`<style>` in `<head>`, `<script>` before `</body>`)
- **Dark color palette**: deep navy background (`#1a1a2e` or `#0d1b2a`), bright accent colors, light text
- **No external dependencies**: no CDN links, no web fonts, no images — emoji for illustration
- **Vanilla JS**: `document.getElementById`, `addEventListener`, direct DOM manipulation — no libraries
- **State as plain variables**: simple `let` variables for state, a `render()` function that redraws from state

### Pakistan Adventure (`pakistan-adventure.html`) specifics

- Scenes are plain JS objects: `{ id, location, emoji, text, choices: [{label, next}], isEnding, endingTitle }`
- All scenes live in a single `SCENES` object keyed by scene ID
- State: `currentScene` (string) + `history` (array of scene IDs for the back button)
- `render()` reads `SCENES[currentScene]` and redraws the card, breadcrumb, and choice buttons
- Navigation: `goTo(id)` pushes to history; `goBack()` pops; `restart()` resets both
- 13 scenes total: `start → hunza/ruins/lahore → [2 sub-scenes each] → [3 endings]`
