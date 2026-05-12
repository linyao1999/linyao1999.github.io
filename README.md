# Personal Website

A clean, single-file academic homepage. No build step, no dependencies — just `index.html` plus an `assets/` folder.

## File layout

```
.
├── index.html          # Whole site (HTML + embedded CSS)
├── assets/
│   ├── profile.jpg     # Your headshot (add this)
│   └── cv.pdf          # Your CV (add this)
└── README.md
```

## Customizing

The site is pre-populated from your UChicago profile and Google Scholar. The placeholders that still need your input are bracketed — search the file for `[` to find them. The remaining ones are:

- `[Postdoc Institution]` and `[Month Year]` — where you're heading and when (appears in the hero affiliation, the bio, and the CV positions block)
- `[Undergraduate Institution]` and the `[year]–[year]` range — the BSc entry in the CV
- `[coauthors]` and `[coauthor]` in the publications — fill in actual coauthor names
- The publication links currently point to `#` — drop in real DOI / PDF URLs

Other things you'll likely want to update:

- The `<div class="photo">LY</div>` block — replace with `<img class="photo" src="assets/profile.jpg" alt="Lin Yao">` once you've added a photo (drop the file in `assets/profile.jpg`)
- Add your CV at `assets/cv.pdf` — the "Download CV" button already links there
- GitHub and ORCID social links currently point to the bare domains — paste in your real handles/IDs
- The office address is set to UChicago Hinds Lab; once you move to your postdoc, update it

## Preview locally

From this folder:

```bash
python -m http.server 8000
```

Then open http://localhost:8000.

## Deploy on GitHub Pages

1. Create a new public repo named **`<your-username>.github.io`** (this gives you a clean URL).
2. Push these files to the `main` branch:
   ```bash
   git init
   git add .
   git commit -m "Initial site"
   git branch -M main
   git remote add origin git@github.com:<your-username>/<your-username>.github.io.git
   git push -u origin main
   ```
3. In the repo on GitHub: **Settings → Pages → Source: Deploy from branch → Branch: main / root**.
4. Wait ~1 minute. Site goes live at `https://<your-username>.github.io`.

If you'd rather host it as a *project* page (e.g. `username.github.io/website`), just name the repo anything — the same Pages settings apply, and the URL becomes `https://<your-username>.github.io/<repo-name>`.

## Custom domain (optional)

If you have a domain like `linyao.com`:

1. Add a `CNAME` file containing just `linyao.com` to the repo root.
2. At your DNS provider, point an `A` record at GitHub Pages' IPs (185.199.108.153, 185.199.109.153, 185.199.110.153, 185.199.111.153) — or a `CNAME` to `<your-username>.github.io` for `www`.
3. Back in **Settings → Pages**, set the custom domain and tick "Enforce HTTPS" once the cert provisions.

## Notes

- The site has light + dark mode already (follows the visitor's OS setting).
- The layout is responsive — works on phones.
- Fonts are loaded from Google Fonts (Inter + Crimson Pro). If you want to keep things fully self-hosted, download them and swap the `<link>` tag for a local `@font-face`.
