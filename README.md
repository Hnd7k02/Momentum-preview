# Momentum — temporary preview

Built output only, for real-device visual QA of `Momentum-App` branch
`claude/momentum-wp3` before it is merged. No source, no history.

- Built from commit `b46c44b` (Momentum-App, WP3 Stage 5b as the owner accepted it at STOP 5b, with his answers built: a Gym exercise-day is worth its best working set by a strength score, load × (1 + reps ÷ 30), from the first load of this build on, as an era — every day before it replays as it did. A range compares the median of an exercise's last days with the median of its first, which he confirmed. A set can be marked as a warm-up by tapping its number, and a hint under the sets says so until a set has been marked once. The exercise detail draws a line where it drew bars: each day as its change since the first day shown. It also carries block 7A's body with the owner's addendum, and the colour rules of the muscle status) with `--base=/Momentum-preview/` and `VITE_MOMENTUM_DB=momentum-preview`, on 2026-11-15.
- **For the check of Stage 5b** the owner imports
  `docs/wp3/stage5b/momentum-pruefdaten-5b.json` from `Momentum-App` — five
  invented weeks of training, made by the live build itself — here and into
  the live app, and compares the two.
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
- `models/momentum-body.glb` (690 KB, 480 KB as transferred) and the lazy `assets/BodyViewer-*.js`
  chunk are published: the 3D body in Bereiche → Gym fetches both on first
  entry.
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
