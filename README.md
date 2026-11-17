# Momentum — temporary preview

Built output only, for real-device visual QA of `Momentum-App` branch
`claude/momentum-wp3` before it is merged. No source, no history.

- Built from commit `b71cf9e` (Momentum-App, branch `claude/momentum-wp3`, application source `017cc56`): **the WP3 release candidate** at the gate of block 9 (STOP 9, 2026-11-17) — WP3 as a whole, Mind and Gym, with block 9's changes: a workout saved on a day still open shows at once in the Gym rating, in Verlauf and in a question's history, marked «vorläufig» until the day is complete (D194); with less transparency the tab bar, the bar of a workout and a sheet's scrim turn solid too (D195). Built with `--base=/Momentum-preview/` and `VITE_MOMENTUM_DB=momentum-preview`.
- **For the check of the release candidate** the owner works through `docs/device-tests.md` in `Momentum-App`. There is no backup with real data: import the file of the day you check from `docs/wp3/stage9/` (`momentum-pruefdaten-9-2026-11-17.json` on 17 November, `…-18.json` on the 18th, `…-19.json` on the 19th) — files made by the live app itself, so the import is the update on that day. The onboarding can still be walked as a rehearsal: Bereiche → Einstellungen → «Einführung ansehen», a row only this preview has.
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
