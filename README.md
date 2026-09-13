# GRRRLHOOD

For women in the in-between. Landing page + manifesto for the GRRRLHOOD waitlist.

Live at **https://grrrlhood.co**

## Structure

```
index.html            Homepage (deploy copy — served at /)
manifesto/index.html  Manifesto page (deploy copy — served at /manifesto/)
Grrrlhood.dc.html      Homepage source (Claude Design component)
Manifesto.dc.html      Manifesto source (Claude Design component)
support.js             Claude Design component runtime (do not edit by hand)
uploads/               Design assets
CNAME                  GitHub Pages custom domain config
.nojekyll               Tells GitHub Pages not to run Jekyll on this repo
_redirects / vercel.json  Clean-URL rewrites for Netlify/Vercel (unused on GitHub Pages)
```

Static site, no build step. `support.js` loads React/ReactDOM from a CDN at runtime and
renders the `.dc.html` templates client-side.

**Editing:** change the `.dc.html` source files, then copy the result into `index.html` /
`manifesto/index.html` (adjusting relative paths — `manifesto/index.html` is one level
deeper, so its links to `support.js` and to the homepage use `../`).

## Run locally

```bash
python3 -m http.server 8000
```

Then open `http://localhost:8000/`.

## Deploy

Pushes to `main` publish automatically via GitHub Pages
(repo: `iremkaraer-debug.github.io`). Custom domain DNS is configured in Cloudflare
(A records → GitHub Pages IPs, `www` CNAME → `iremkaraer-debug.github.io`).

## Known TODO

- [ ] Wire the waitlist form (`Grrrlhood.dc.html` / `index.html`, `onJoin`) to a real
      endpoint (Formspree) — it currently only toggles a local confirmation state and
      does not persist submissions anywhere.
