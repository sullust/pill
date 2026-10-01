# Pills Left

A one-screen tracker for a 30-pill supply. It shows the date you'll run out (today plus one day per pill left), lets you log each pill with **Took a pill**, and **Reset to 30** after a refill (tap twice to confirm). Below that are a blister-pack view of the supply and a day-by-day log.

Live app: https://claude.ai/artifact/UqqYWXqzEZcTRZ3gGMx9a4

## How it saves

The app runs as a Claude.ai Artifact with the `artifact` capability. Each tap rebuilds the whole page with the new count and log embedded in `<script id="seed">` and publishes it as a new version, so every browser signed in to your Claude account sees the same data. Opened anywhere without the Claude runtime (for example straight from this repo), it falls back to saving in that browser only and says so.

`index.html` is the page exactly as Claude.ai serves it. To republish from this file, send only the content between `<body>` and `</body></html>` to the Artifact tool; the page rebuilds the same skeleton itself when it saves.
