# Momentum — temporary preview

Built output only, for real-device visual QA of `Momentum-App` branch
`claude/momentum-wp3` before it is merged. No source, no history.

- Built from commit `67db6d2` (Momentum-App, WP3 — the colour rules of the muscle status, contract §7: a change is held from −2 % to +2 % and coloured from ±3 %, a group states a trend only with three exercise days, "Gehalten" is neutral and white on the body, Muskelgruppen reads 30 or 90 days, "Leistungstrend" and "Zu wenig Vergleichsdaten", the legend behind ⓘ) with `--base=/Momentum-preview/` and `VITE_MOMENTUM_DB=momentum-preview`, on 2026-11-11.
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
- `models/momentum-body.glb` (467 KB) and the lazy `assets/BodyViewer-*.js`
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
