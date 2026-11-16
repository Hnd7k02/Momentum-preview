# Momentum — temporary preview

Built output only, for real-device visual QA of `Momentum-App` branch
`claude/momentum-wp3` before it is merged. No source, no history.

- Built from commit `c24c8d4` (Momentum-App, WP3 block 7B at its STOP on 2026-11-16, waiting for the owner's check: Muskelgruppen is the body's stage — no card, 55 % of the visible height, a strip of three figures above it; a tap never turns the body and reaches a group from twelve pixels beside it; the motion counts time, not frames; two fingers zoom to 1.8, a double tap and a button reset; a sheet stands over a still body; a lost graphics context ends with the body or the flat figure; Heute's Gym label leads straight to the body and back leads to Heute. It carries a measuring display — off until switched on under Bereiche → Einstellungen → "Messanzeige beim Körper" — that shows how fast the body loads and how smoothly it turns and copies the values as text. It also carries block "Kurve" and Stage 5b as the owner accepted them, block 7A's body with his addendum, and the colour rules of the muscle status) with `--base=/Momentum-preview/` and `VITE_MOMENTUM_DB=momentum-preview`, on 2026-11-16.
- **For the check of block 7B** the owner imports the file of his check day
  from `docs/wp3/stage7b/` in `Momentum-App` — the invented diary of the
  block "Kurve", made anew by the live build itself, the last session on
  that day: `momentum-pruefdaten-7b-2026-11-16.json` on 16 November,
  `…-2026-11-17.json` on the 17th, `…-2026-11-18.json` on the 18th. In this
  diary every group is rated and improved; the empty screen is this
  preview before any import. There is no backup with real data.
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
