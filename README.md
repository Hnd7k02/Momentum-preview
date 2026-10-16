# Momentum — temporary preview

Built output only, for real-device visual QA of `Momentum-App` branch
`claude/momentum-wp3` before it is merged. No source, no history.

- Built from commit `188ff3d` (Momentum-App, WP3 Stage 3b: one day back — Heute | Gestern, today and yesterday for every write, a week judged when it is over, a pending abstinence charge, promotions on settled days) with `--base=/Momentum-preview/`, on 2026-10-16.
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
emits: it carries `apple-mobile-web-app-status-bar-style: black-translucent`,
which is the only style under which the web view reaches the physical top
edge and `env(safe-area-inset-top)` becomes a real value. That fix lives here
and has never been in `Momentum-App`, whose `index.html` still says
`default`. Only the two asset URLs are rewritten on each publish, so a
rebuild cannot quietly undo it — and the preview shows the safe-area
behaviour a real device actually has.

The files sit at the repository root, so **either** Pages source works:
*Deploy from a branch* (`main`, `/ (root)`) or *GitHub Actions* (re-run the
`Publish preview` workflow).

Delete this repository once the review is done.
