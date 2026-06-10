# World Cup Pool Draw

A live, single-file draw application for a tiered family World Cup pool. Built for screen-sharing on Google Meet — five players, forty-eight teams, four tiers and a final pool.

Originally made for the **Casa Baglioni** 2026 family draw. Free for anyone to fork and run their own.

## What it does

Five players each pick teams from a pre-prepared "hat" of 48 World Cup nations. The mechanic:

- **48 teams** are split into 4 tiers of 12 (favorites, contenders, dark horses, underdogs) based on FIFA rankings and betting markets.
- Tiers are drawn one at a time. Each player picks **2 teams per tier**. The 2 unpicked teams from each tier accumulate into a "pool."
- After all four tiers, the **pool of 8 teams** is drawn. Each player picks **one** from the pool. The remaining 3 teams go to **The House** — a special split-pot entity.
- Each player ends with **9 teams**. The House holds 3 teams; if any of those teams wins the tournament, the pot is split evenly among all players.

Each player also gets **one redo token** — a single-use mulligan they can spend to re-roll any one of their own picks during the draw.

## Stack

Vanilla HTML / CSS / JavaScript in a single file. No build step, no dependencies, no server required.

- Slot-machine spinner with deceleration physics
- Auto-save to `localStorage` (refresh-proof)
- Full-screen team reveals with per-team flag colors
- Live pick-order shuffle animation between rounds
- End-of-round recap screens
- Brutalist aesthetic — monospace data, hard borders, off-white surfaces, international orange for active moments

## Run it locally

Double-click `index.html`. That's the whole instruction.

For your actual draw, the file uses `localStorage` to auto-save so you can refresh mid-draw and resume exactly where you left off. The clipboard "Copy" feature on the final screen requires HTTPS (or `localhost`), so for the live draw running from your local filesystem the Download button is the more reliable export.

## Customize it for your family

The Casa Baglioni branding is hardcoded in a few places. To make it yours:

- **Family name** — search `Casa Baglioni` in `index.html`. There are a few text uses (brand bar, page title, results header).
- **Page title and meta** — top of `index.html` in the `<head>`.
- **Crest** — replace `crest.svg` with your own family / club crest. Any square SVG works (the one shipped is 1254×1254). The intro screen will scale it.
- **localStorage key** — search `casa-baglioni-draw-v1` if you want a different key (mostly cosmetic — only matters if you've already played a draw under the old key and want a clean start).
- **The teams** — search `const TIERS` to swap teams or tier names. The mechanic assumes 4 tiers of 12 but the code itself doesn't enforce that — you could change to 3 tiers of 10, etc., though some numbers in the spinner deceleration are tuned for 12-team tiers.
- **Player count** — currently hardcoded to 5 in the setup screen. The pool math (5 picks of 8, 3 to House) assumes 5 players.

## Deploy

It's a static HTML file — any static host works.

- **Netlify Drop**: drag the folder to https://app.netlify.com/drop.
- **Vercel**: `npm i -g vercel && vercel` from this directory.
- **GitHub Pages**: Settings → Pages → enable from `main`.
- **Cloudflare Pages**: connect this repo at https://dash.cloudflare.com.

All four give you HTTPS and a free subdomain.

## File layout

```
index.html      The entire app (HTML + CSS + JS, ~94 KB)
crest.svg       The intro screen crest (replace with your own)
LICENSE         MIT
README.md       This file
```

## License

MIT. See [`LICENSE`](./LICENSE).

---

Built by [Andrea Baglioni](https://github.com/) with [Claude](https://claude.ai). If you fork it and run a successful family draw, I'd love to hear about it.
