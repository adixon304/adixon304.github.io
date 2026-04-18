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

The aesthetic is intentionally minimal. Do not add decorative elements, shadows, gradients, or visual complexity.

- **Background:** sage green `#588157`
- **Text:** white `#fff`
- **Font:** Helvetica
- **Layout:** CSS Grid, 2 equal columns, full-viewport centering (`place-items: center; height: 100vh`)

Do not change the color palette or introduce JavaScript or additional libraries beyond Jekyll.

## Content Structure

Single page with two columns:
- **Left:** profile image
- **Right:** name (`h1`), title/employer (`h2`), short bio (`p`)

Content is currently hardcoded in `index.html`. With Jekyll, it will move to `_config.yml` or front matter.
