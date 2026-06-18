# Jarvis Poker — Claude Code guidelines

Old-school *Jacks or Better* video poker. Part of the Jarvis constellation
(sibling of Stellar Ascent & Space Base Race).

## Project shape
- Single-file `index.html` — vanilla JS + CSS, **no framework, no build step**.
  All game logic, UI, audio, and styles live in `index.html`.
- `.jarvis.json` declares the project for the Jarvis Launcher + Dashboard registry.
- `readme`/changelog and the in-game footer version (`VERSION` const) stay in sync.
- Preview server: `python3 -m http.server 3000` (see `.claude/launch.json`).

## Branch strategy & permissions
- `dev` — active development. Edit, commit, and `git push origin dev` freely.
  Pushing `dev` triggers the Pages deploy → published at `/dev/`.
- `main` — production (`https://poker.dabrewer.dev/`). **Promote only via a PR the
  user approves** — never push, fast-forward, or force-push `main` directly.
- Always ask before: deleting branches, force-pushing, or merging into `main`.

## Deploy pipeline
`.github/workflows/pages.yml` lives on `dev` and checks out *both* branches:
`main` → site root `/`, `dev` → `/dev/`, writing the `poker.dabrewer.dev` CNAME.
Pushing to `main` does **not** auto-deploy — re-run the workflow or push `dev`.

## Repo
`BrewerIndustries/poker` (public, for GitHub Pages).
