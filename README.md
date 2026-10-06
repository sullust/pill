# Pills Left

A one-screen tracker for a 30-pill supply. It shows the date you'll run out (today plus one day per pill left), lets you log each pill with **Took a pill**, and **Reset to 30** after a refill (tap twice to confirm). Below that are a blister-pack view of the supply and a day-by-day log.

Live app: https://claude.ai/artifact/UqqYWXqzEZcTRZ3gGMx9a4

## Files

- `pills-left.html` — the app, exactly as Claude.ai serves it.
- `index.html` — a launcher for GitHub Pages that gives the app a 💊 home-screen icon on iPhone.
- `apple-touch-icon.png` (180×180) and `icon-512.png` — the icon, rendered from the Noto Color Emoji 💊 (Apache License 2.0).

## How the app saves

The app runs as a Claude.ai Artifact with the `artifact` capability. Each tap rebuilds the whole page with the new count and log embedded in `<script id="seed">` and publishes it as a new version, so every browser signed in to your Claude account sees the same data. Opened anywhere without the Claude runtime, it falls back to saving in that browser only and says so.

A daily Claude routine ("Pills Left daily GitHub sync", 12:23 UTC) copies the live app's data into `pills-left.html` here, committing only when it changed, so the repo keeps a history of the log.

To republish from `pills-left.html`, send only the content between `<body>` and `</body></html>` to the Artifact tool; the page rebuilds the same skeleton itself when it saves.

## Home-screen launcher

An iPhone takes a home-screen icon from the page you add, and Claude.ai's page always gives artifacts a generic icon. The launcher is a page this repo controls, with its own icon, that forwards to the app.

- Opened normally, it shows an **Open Pills Left** button and quietly changes its address to `?launch=1`, so that's the address **Add to Home Screen** saves.
- Opened at `?launch=1` (or as a home-screen web app), it forwards straight to the app.

Turn **Open as Web App** off when adding it, so the shortcut opens in Safari, where you're already signed in to Claude.

### Turning on GitHub Pages

Settings → Pages → Build and deployment → Source: **Deploy from a branch**, then pick the branch that holds these files and the **/ (root)** folder, and save. The launcher is then at https://sullust.github.io/pill/.

GitHub Pages only serves private repositories on a paid plan. On a free plan, make the repository public first; it holds only the app's code and the launcher, not your pill log, and the app link still requires your Claude login.
