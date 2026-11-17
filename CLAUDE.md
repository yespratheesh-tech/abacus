# Abacus Adventures

A kids' website for learning the soroban (Japanese abacus: 1 heaven bead worth 5, 4 earth beads worth 1 per rod).
Built for my daughter. Keep the tone friendly and simple for a child; use Australian English.

## Layout
- `public/index.html`: the whole site, one self-contained page (HTML + CSS + JS, no build step, no dependencies besides Google Fonts).
- `wrangler.jsonc`: Cloudflare Worker serving `./public` as static assets. `name` must match the Worker in the Cloudflare dashboard.

## How the code is organised (inside index.html)
- `Soroban` class: renders an SVG abacus (`rods`, `interactive`, `labels`, `onChange`); digits stored in `this.D` (left = highest place).
- `Solver`: turns a sum into bead moves (`ops` with `col`, `delta`, `tag`, `say`), using the soroban techniques direct / small friend (5) / big friend (10) / mixed. Works left to right.
- `Player`: steps through solver ops on an abacus with explanations.
- Views use hash routing: #home #learn #simulator #practice #flash #worksheets #quiz.
- `LEVELS` defines the practice/worksheet generators; problems are filtered by the solver's technique tags.
- Stars are kept in localStorage (wrapped in try/catch).

## Deploy
Push to `main`. Cloudflare Workers Builds runs `npx wrangler deploy`.
Local check: open public/index.html in a browser, or run `npx wrangler dev`.

## When changing things
- Keep it one file with no build step.
- After changing the Solver, check that random sums still give the right answers and only legal bead moves.
