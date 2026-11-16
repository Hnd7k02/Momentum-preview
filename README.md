# Momentum — temporary preview

Built output only, for real-device visual QA of `Momentum-App` branch
`claude/momentum-wp3` before it is merged. No source, no history.

- Built from commit `4a61baf` (Momentum-App, WP3 block 7C at its STOP on 2026-11-16, waiting for the owner's check: a tap on a muscle of the body or on a group's row opens the group's sheet — two thirds of the screen, dragged up to 92 % and down to close, closed by the cross, by a tap on the body above it, by Escape and by Back; the body above the sheet shows the group and stands still; in the sheet stand the row's own figure and state, the group's line, its exercises each with one change, and the work volume per week, "nicht gewertet"; an exercise's detail lies on top and Back walks step by step; the card "Muskelgruppen" on the Gym hub holds its place while it loads, and all lines of the ten rows stand in one column. It also carries block 7B — the body's stage, and the measuring display under Bereiche → Einstellungen → "Messanzeige beim Körper" — block "Kurve" and Stage 5b as the owner accepted them, block 7A's body with his addendum, and the colour rules of the muscle status) with `--base=/Momentum-preview/` and `VITE_MOMENTUM_DB=momentum-preview`, on 2026-11-16.
- **For the check of block 7C** the owner imports the file of his check day
  from `docs/wp3/stage7c/` in `Momentum-App`:
  `momentum-pruefdaten-7c-2026-11-16.json` on 16 November,
  `…-2026-11-17.json` on the 17th, `…-2026-11-18.json` on the 18th. It is
  the device the block's checks and pictures run on, with every state a
  group can be in — a change, "uneinheitlich", too little to compare, not
  trained, a single observation — exported by the build through its own
  interface. Its rows were written by a script, not typed: Muskelgruppen,
  the sheets, the exercise details and the Gym hub's card are what it is
  for; Heute, Verlauf and Rang show a device nobody lived on. The diary
  files of block 7B (`docs/wp3/stage7b/`) are still right on the same
  days, for a diary in which every group is rated and improved. There is
  no backup with real data.
- **This preview keeps its data in a database of its own**, `momentum-preview`.
  The live app is served from the same origin
  (`hnd7k02.github.io/Momentum-App/`), and pages of one origin share their
  databases in a browser; up to the Stage 6b publish the preview opened the
  live app's `momentum`. From this build on it cannot touch it. The preview
  therefore **starts empty**: import a backup in Einstellungen to see your
  own data here.
- `sw.js` is deliberately **not** published. Its precache list now follows
  the build's base, so it would be right here — but without it every load is
  fresh, which is what a visual review wants. It also means the PWA/offline
  path cannot be tried on this preview; that stays for the production site.
- `models/momentum-body.glb` (690 KB, 480 KB as transferred), the lazy
  `assets/BodyViewer-*.js` chunk and the body's still
  `assets/body-stage-*.webp` are published: Muskelgruppen shows the still
  at once and fetches the other two when it is opened — from Heute's Gym
  label or from the Gym hub. Heute itself fetches neither.
- The sourcemap is omitted for the same reason — it is not needed to look at
  the app.

`index.html` is **the preview repository's own**, not the one the build
emits; only the two asset URLs are rewritten on each publish.

**Its status-bar style is `default`**, as in `Momentum-App` — decided at
STOP 6b for the rest of WP3 (D149, D163): iOS paints the status bar from
`theme-color`, which the app sets per world, light in Mind and dark in Gym.
Up to and including the Stage 4 publish this file carried
`black-translucent`, the only style under which the web view reaches the
physical top edge. An edge-to-edge status bar is a backlog item of its own,
with its catch: under `black-translucent` the bar's own text is always
white for a Home Screen app. An app already on the Home Screen keeps the
style it was added with: remove it and add it again after a change.

The files sit at the repository root, so **either** Pages source works:
*Deploy from a branch* (`main`, `/ (root)`) or *GitHub Actions* (re-run the
`Publish preview` workflow).

Delete this repository once the review is done.
