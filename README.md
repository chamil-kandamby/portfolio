# chamil.around2.com

Personal portfolio. One static page (`index.html`) styled with around2's
Classical theme. No build step and no dependencies apart from Google Fonts.

## Preview locally

```bash
cd ~/PersonalSource/portfolio
python3 -m http.server 8088 --bind 127.0.0.1
# open http://127.0.0.1:8088/
```

## Deploy (GitHub Pages + DigitalOcean DNS)

Hosted on GitHub Pages and kept separate from the around2 App Platform app,
so publishing the portfolio never triggers an around2 deploy.

1. Create a **public** repo `chamil-kandamby/portfolio` and push `main`.
   (Pages on a private repo needs a paid GitHub plan.)
2. Repo → Settings → Pages → *Deploy from a branch* → `main` / `/ (root)`.
   The `CNAME` file already sets the custom domain to `chamil.around2.com`.
3. DigitalOcean → Networking → Domains → `around2.com` → add a record:
   `CNAME` · hostname `chamil` · value `chamil-kandamby.github.io.` · TTL 3600.
   A specific record wins over the `*.around2.com` wildcard for that one name;
   around2.com and every other subdomain keep pointing at App Platform.
4. Once DNS resolves, tick **Enforce HTTPS** in the Pages settings.
5. Recommended: Settings (account) → Pages → *Verified domains* → add
   `around2.com` and create the TXT record GitHub shows. Without this, someone
   else could claim the subdomain on GitHub if the Pages site is ever removed.

## Editing

- Content comes from the LinkedIn export `~/Downloads/Profile.pdf`
  (October 2026). No GitHub projects or links, and no employer or client
  company names: roles, years, countries and the kind of work only.
- Colour and type tokens are copied from `around2/resources/css/app.css`.
  That file is the source of truth; keep the `:root` block in step with it.
- The experience bars are drawn by the script at the bottom of `index.html`
  from each row's `data-from` / `data-to` (`YYYY-MM` or `now`).
- `_drafts/` (git-ignored, never published) holds sections taken off the page,
  with restore notes. Currently: Selected projects, and `portrait-edit.py`,
  the script that made `assets/portrait.jpg` (background blurred so the shop
  sign behind is unreadable, light colour correction, metadata stripped).
