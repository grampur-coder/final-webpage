# FluidSim2D — Final Report

Static one-page report site for the CS 184/284A Spring 2026 final project.

This folder is fully self-contained. It is just an `index.html` plus an optional `media/` folder for screenshots and the demo clip. Drop your assets into `media/` and deploy the folder anywhere static.

## Layout

```
report/
├── index.html        # the report page
├── media/            # (you create this) screenshots + showcase clip
│   ├── showcase.mp4
│   ├── poster.jpg
│   ├── sim-1.png
│   ├── sim-2.png
│   ├── benchmark.png
│   └── aa.png
└── README.md         # this file
```

The page references the media files by relative path, so they will work in any static host.

## Editing the report

Open `index.html` in any editor. Things you will likely want to update:

- The `[Edit me]` blocks under **Contributions** at the bottom.
- The footer GitHub link.
- The placeholder screenshots in the **Results** section.
- Anything else you want to expand on (results, benchmarks numbers, etc).

The math is rendered with MathJax, so you can write LaTeX directly in the page if you want to add more equations.

## Local preview

You can open `report/index.html` directly in a browser, or serve it with any static server. For example:

```
cd report
python3 -m http.server 5500
# then visit http://localhost:5500/
```

## Deploying to Vercel

The simplest path:

1. Sign in at <https://vercel.com>.
2. Click **Add New… → Project**.
3. Either import your GitHub repo and set the **Root Directory** to `report`, or drag the `report/` folder onto the dashboard.
4. Framework preset: **Other**. Build command: leave blank. Output directory: `.`.
5. Click **Deploy**. You'll get a `*.vercel.app` URL.

CLI alternative, from inside the `report/` directory:

```
npm i -g vercel
cd report
vercel deploy --prod
```

When asked for the project settings, accept the defaults. The `report/` folder will be served as a static site.

## Deploying to GitHub Pages

Two common options.

**Option A — `report/` as the site root of a `gh-pages` branch**

```
git checkout --orphan gh-pages
git rm -rf .
cp -R ../path/to/report/. .
git add .
git commit -m "Publish FluidSim2D report"
git push origin gh-pages
```

Then in your repo go to **Settings → Pages** and select the `gh-pages` branch, root folder `/`.

**Option B — keep everything on `main` and serve from `/docs`**

GitHub Pages can serve from `main` branch, `/docs` folder. Rename the folder:

```
mv report docs
git add docs
git commit -m "Publish FluidSim2D report under /docs"
git push origin main
```

Then **Settings → Pages → Branch: main, folder: /docs**.

After enabling Pages, the site will appear at `https://<your-username>.github.io/<repo-name>/`.

## Adding the showcase clip

The Results section embeds `media/showcase.mp4`. To add yours:

1. Record or export a short clip (mp4, webm, or h.264 mp4 is most compatible).
2. Optionally export a poster image as `media/poster.jpg`.
3. Save it as `report/media/showcase.mp4` and redeploy.

If you only have a GIF, swap the `<video>` tag in `index.html` for an `<img>`:

```html
<img src="media/showcase.gif" alt="FluidSim2D showcase clip" />
```
