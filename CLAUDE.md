# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Tech Stack

Personal portfolio site for Alex Dixon at **alexdixon.me**, served via GitHub Pages.

Built with **Jekyll**, served via GitHub Pages.

```bash
bundle exec jekyll serve   # local dev (http://localhost:4000)
bundle exec jekyll build   # production build → _site/
```

## Deployment & Git Workflow

Push to `main` → GitHub Pages auto-deploys. Jekyll sites build automatically on GitHub Pages — no CI config needed. Custom domain set via `CNAME` (`alexdixon.me`).

Commit often — especially for bug fixes, make a new commit per fix rather than bundling changes. SSH is configured via `~/.ssh/id_ed25519`; if push is rejected, run `ssh-add ~/.ssh/id_ed25519` to re-add the key to the agent (required after restarts).

## Design Intent

Minimal, editorial aesthetic. Sage green `#588157` is the accent color on a neutral background — not a background fill. Restraint still applies: no decorative flourishes, heavy shadows, or gradients.

- **Design tokens:** all colors, fonts, and radii are CSS custom properties in `:root` at the top of `css/style.css`. Always use tokens, never hardcoded colors. Dark theme is a single `html[data-theme="dark"]` token-override block; it follows `prefers-color-scheme` until the nav toggle stores a choice in localStorage.
- **Typography:** Newsreader (headings, prose) + Inter (nav, buttons, tags, meta), loaded from Google Fonts with Georgia/Helvetica fallbacks.
- **Nav:** fixed frosted bar (translucent + backdrop-blur, hairline border) with the "AD" monogram as an inline `currentColor` SVG (`_includes/logo.svg`).
- **JavaScript:** keep it minimal and vanilla — theme toggle, recipe search/filters, and the Formspree contact form are the only scripts. No frameworks or new libraries.
- **Motion:** subtle only (hover lifts, hero entrance fade). Anything animated must respect `prefers-reduced-motion`.

## Content Structure

- **Home** (`index.html`): full-viewport hero — avatar, name, tagline, buttons, and a "Currently" snippet. Currently items live in `_data/currently.yml`; edit that file (not the markup) to update them.
- **About** (`about/index.html`): bio with floated headshot, career timeline (`.timeline`), "How I work" principles, and a candid photo strip (placeholders until real photos land in `images/about/`).
- **Recipes** (`recipes/index.html`): 3 featured cards + searchable/filterable list. Recipes are posts in `_posts/` using the `recipe` layout (ingredients/steps in front matter + body, JSON-LD schema emitted automatically). An optional `story` front-matter field renders as a personal headnote above the ingredients. Recipe images live in `images/recipes/`, compressed to ≤1600px wide / ~200-300KB.
- **Contact** (`contact/index.html`): Formspree-backed form.
- Shared chrome in `_includes/` (nav, footer, logo) and `_layouts/`.

## Voice & Copy Rules

Site copy is Alex's voice. Never use em dashes in copy. Avoid AI-sounding prose (no "delve", no triadic flourishes, no marketing cadence). Any copy drafted by Claude must be flagged for Alex's review before pushing; prefer keeping his phrasing when shaping text he provided.
