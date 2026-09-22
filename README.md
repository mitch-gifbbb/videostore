# Perry's Video Store

Single-file site. `index.html` is the whole thing — data is embedded inside it, so it works from a plain file, GitHub Pages, or Vercel with no build step.

## Hosting
- **GitHub Pages:** put `index.html` in a repo, Settings → Pages → deploy from `main`. Done.
- **Vercel:** drag the folder onto vercel.com/new, or `vercel` from the folder. Framework preset: Other.

## Editing the collection
The data lives in `index.html` inside `<script id="data" type="application/json">…</script>` (one JSON array). `data.json` is the same array on its own for easier editing.

Each title:
```json
{"id":12,"title":"Semi-Pro","year":2008,"type":"Movie","format":"DVD","copies":1,
 "genres":["Comedy","Sports"],"actors":["Will Ferrell","Woody Harrelson","André Benjamin"],
 "director":"Kent Alterman","series":"","photo":[1],"note":"Unrated","check":false}
```
- `type`: Movie, TV, Stand-up, Music, Sports, Documentary, Game
- `format`: DVD, Blu-ray, HD DVD, PS3
- `series`: franchise name, or for TV the seasons owned
- `want`: true = wishlist item, not owned. Shows greyed on the Shelf/List only when the Wishlist chip is on, and always in Series view so gaps are visible. When you buy it, set `want` to false.
- `check`: true shows a red "check" badge — set to false once you've confirmed the row
- `id` must be unique and must never change — watched/rating/notes in the browser are keyed to it

To add a title: append an object with a new `id` to the array in `data.json`, then paste the whole array back between the data script tags in `index.html`.

## Personal data
Watched, ratings, notes and "lent to" are saved in the browser's localStorage under `perrys-video-store-v1`. Use **Export my data** at the bottom of the page before clearing a browser or switching devices, then **Import** on the other one.
