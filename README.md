# chamil.around2.com

Personal portfolio. One static page (`public/index.html`) styled with around2's
Classical theme. No build step and no dependencies apart from Google Fonts.

## Preview locally

```bash
cd ~/PersonalSource/portfolio
python3 -m http.server 8088 --bind 127.0.0.1 --directory public
# open http://127.0.0.1:8088/
```

Everything served lives in `public/`. App Platform finds that folder by name,
and anything outside it (this README, `.gitignore`) is never published.

## Deploy (static site inside the around2 App Platform app)

The site is the `portfolio` static-site component of the around2 app on
DigitalOcean App Platform. An ingress rule sends `chamil.around2.com` to it and
everything else to around2's `web` service. The component's spec is mirrored in
`around2/.do/app.yaml`.

- **Pushing to `main` deploys.** The component has `deploy_on_push`, and every
  deployment of the app also rebuilds around2's `web` service and runs its
  `migrate` pre-deploy job against the live database. Batch changes and push
  once, rather than pushing every small fix.
- **DNS needs nothing.** around2.com's `*.around2.com` wildcard record and the
  app's wildcard domain already send `chamil.around2.com` to the app and cover
  it with TLS. Do not add a separate `chamil` record.
- DigitalOcean's GitHub app must be allowed to read this repo
  (GitHub → Settings → Applications → DigitalOcean → Repository access).

## Editing

- Content comes from the LinkedIn export `~/Downloads/Profile.pdf`
  (October 2026). No GitHub projects or links, and no employer or client
  company names: roles, years, countries and the kind of work only.
- Colour and type tokens are copied from `around2/resources/css/app.css`.
  That file is the source of truth; keep the `:root` block in step with it.
- The experience bars are drawn by the script at the bottom of `public/index.html`
  from each row's `data-from` / `data-to` (`YYYY-MM` or `now`).
- `_drafts/` (git-ignored, never published) holds sections taken off the page,
  with restore notes. Currently: Selected projects, and `portrait-edit.py`,
  the script that made `public/assets/portrait.jpg` (background blurred so the shop
  sign behind is unreadable, light colour correction, metadata stripped).
