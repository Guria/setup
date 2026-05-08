# GitHub Pages publish for dot.guria.dev

This repository publishes the install script via GitHub Pages from the `public/` folder.

## Files

- `setup.sh` — local install script for the repo
- `public/index` — Pages entrypoint for `https://dot.guria.dev`
- `public/setup.sh` — fallback script at `https://dot.guria.dev/setup.sh`
- `public/CNAME` — custom domain configuration
- `public/.nojekyll` — disables Jekyll so extensionless files are served as static assets

## Deployment

1. In GitHub repo settings, enable Pages.
2. Set the source to the `gh-pages` branch and use the root folder.
3. Confirm the custom domain is set to `dot.guria.dev`.
4. Point `dot.guria.dev` DNS to GitHub Pages.

## Usage

Try:

```sh
curl https://dot.guria.dev/setup.sh | sh
```

If root delivery does not work for your Pages setup, use the fallback script above.
