# Abacus Adventures

An interactive website for learning the soroban (Japanese abacus): lessons, a step-by-step simulator, practice levels, flash sums, worksheets and a quiz.

## Deploy

Static site served by a Cloudflare Worker (static assets).

```bash
npx wrangler deploy
```

Or connect this repo to a Worker in the Cloudflare dashboard (Workers Builds) and it deploys on every push. The `name` in `wrangler.jsonc` must match the Worker's name.

## Structure

```
wrangler.jsonc     Worker config: serves ./public as static assets
public/index.html  The whole site (single self-contained page)
```
