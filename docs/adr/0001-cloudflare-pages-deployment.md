# Deploy to Cloudflare Pages, not Vercel

The Fuwari template ships pointed at Vercel (`vercel.json`, `astro.config.mjs` site URL defaults to `fuwari.vercel.app`). We're deploying to Cloudflare Pages instead: its free tier has no bandwidth cap (Vercel/Netlify Hobby tiers cap around 100GB/month), and Cloudflare Workers has the more mature edge-WASM story, which matters for a planned future interactive WASM section. The site builds fully static (no `output`/`adapter` set in `astro.config.mjs`), so no adapter change was needed to make this switch.

For now we're using Cloudflare's auto-assigned `*.pages.dev` subdomain rather than a custom domain — adding a custom domain later is a non-breaking, same-day change (DNS CNAME + automatic SSL in Cloudflare Pages project settings), so there's no cost to deferring it.
