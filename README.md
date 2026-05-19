# neobee data solutions — website

The marketing site for **neobeedata.com**. Plain HTML / CSS / JavaScript — no
build step required to view or deploy.

> **Working with Claude Code on this project?** Read these first:
> - **[WORK_HISTORY.md](WORK_HISTORY.md)** — what's been built, why, and what broke along the way.
> - **[ROADMAP.md](ROADMAP.md)** — what's next, ideas to propose, and hard rules you must not violate.

## File map

Everything inside `public/` is what gets deployed — that's the live site.
Everything outside `public/` is local-only tooling.

| File / folder                       | What it is                                            |
| ----------------------------------- | ----------------------------------------------------- |
| `public/index.html`                 | The entire one-page site. Edit copy here.             |
| `public/styles.css`                 | All visual styling (brand colors live in `:root`).    |
| `public/script.js`                  | Mobile menu, sticky header, contact-form submission.  |
| `public/assets/`                    | Logos, favicons, OG share image.                      |
| `public/sitemap.xml`, `robots.txt`  | SEO essentials.                                       |
| `public/_headers`                   | Cloudflare Pages cache + security headers.            |
| `public/site.webmanifest`           | PWA manifest (lets phones add the site to home).      |
| `wrangler.jsonc`                    | Tells Cloudflare to deploy only `public/`.            |
| `scripts/`                          | One-off Node scripts to (re)generate image assets.    |

## Edit copy

Open `public/index.html` in any text editor (VS Code, Notepad++, even
Notepad). Most of what visitors see lives between `<!-- ===== HERO ===== -->`
and the footer comments — search those to find the section you want to
change, edit the text, save, and refresh the browser.

## Preview locally

```sh
# from this folder, serve the public/ directory
npx --yes http-server public -p 4321 -c-1
# or, if Python is installed
cd public && python -m http.server 4321
```

Then open <http://127.0.0.1:4321>.

## Regenerate brand images

If you ever swap the source logo, replace `assets/logo-full.jpg` and run:

```sh
node scripts/extract-bee.mjs   # re-cuts the bee mark PNG
node scripts/build-images.mjs  # regenerates favicons, og-image, etc.
```

`sharp` and `puppeteer` are dev-only; install them with `npm install`.

## Deploy

See [DEPLOY.md](DEPLOY.md) for the full Cloudflare Pages + Squarespace DNS
walkthrough.
