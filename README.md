# Momentum — temporary preview

Built output only, for real-device visual QA of `Momentum-App` branch
`claude/momentum-wp3` before it is merged. No source, no history.

- Built from commit `6447ba8` (Momentum-App, WP3 Stage 6b: variant B is the one design system and the visual contract is applied to every existing screen — colour with three jobs, the type and figure steps, one 16px margin, one order of buttons, the chart rules; nothing computed changed) with `--base=/Momentum-preview/`, on 2026-11-11.
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

**For the Stage 6b acceptance its status-bar style is `default`**, as in
`Momentum-App` (D149): iOS then paints the status bar from `theme-color`,
which the app sets per world — light in Mind, dark in Gym — and whether that
reads well in the Safari tab and from the Home Screen is one of the things
this build is published to settle. Up to and including the Stage 4 publish
this file carried `black-translucent`, the only style under which the web
view reaches the physical top edge and `env(safe-area-inset-top)` becomes a
real value. If `default` is not accepted on the device, the line goes back.
An app already on the Home Screen keeps the style it was added with: remove
it and add it again to see this one.

The files sit at the repository root, so **either** Pages source works:
*Deploy from a branch* (`main`, `/ (root)`) or *GitHub Actions* (re-run the
`Publish preview` workflow).

Delete this repository once the review is done.
