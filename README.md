# Momentum — temporary preview

Built output only, for real-device visual QA of `Momentum-App` branch
`claude/momentum-wp3` before it is merged. No source, no history.

- Built from commit `35a5c9c` (Momentum-App, WP3 block 7D at its STOP on 2026-11-16, waiting for the owner's check: the exercise catalogue holds 135 exercises where it held 49 (the last two, the Bayesian cable curl and the biceps machine, added at the owner's request after the STOP) — at least ten for every muscle group by its primary role, every one with its equipment and its movement — and the picker searches all of it, in a workout and in the plan editor: by name, detail, muscle group with everyday words, movement and equipment, whatever the case or the spelling of an umlaut, by the beginning of a word, every further word narrowing. Without a query the list stands under one heading per group; a query that finds nothing says so and offers "Eigene Übung" with the word as its name. It also carries block 7C with the owner's answers at its STOP — the muscle sheet, every line from its baseline, an exercise's line as its change day by day — block 7B's stage and the measuring display under Bereiche → Einstellungen → "Messanzeige beim Körper", block "Kurve" and Stage 5b as the owner accepted them, block 7A's body with his addendum, and the colour rules of the muscle status) with `--base=/Momentum-preview/` and `VITE_MOMENTUM_DB=momentum-preview`, on 2026-11-16.
- **For the check of block 7D** the owner imports the file of his check day
  from `docs/wp3/stage7d/` in `Momentum-App`:
  `momentum-pruefdaten-7d-2026-11-17.json` on 17 November,
  `…-2026-11-18.json` on the 18th. It was made by the live app's build with
  its own catalogue — the training diary of the earlier STOPs, a plan
  "Oberkörper" and an exercise of the user's own, "Zercher Squat" — so it is
  an existing device: after the import the preview offers 136 exercises and
  shows the same Gym rating as the build before the block (821 on the 17th,
  807 on the 18th). There is no backup with real data.
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
