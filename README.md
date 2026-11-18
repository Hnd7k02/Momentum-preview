# Momentum — temporary preview

Built output only, for real-device visual QA of `Momentum-App` branch
`claude/momentum-wp3` before it is merged. No source, no history.

- Built from commit `e185f91` (Momentum-App, branch `claude/momentum-wp3`, application source `f9848b6`): **the WP3 release candidate after the tidy-up**, the last block of WP3 (2026-11-18, D196–D201). What is new against the candidate of STOP 9: the onboarding chooses nothing for the user — no question, no weekly target, «Weiter» waiting with a sentence until Mind has a question and Gym a target, the second slide naming Gym's target in a sentence (D197); the first slide's picture with its example values a little higher (D201); the new app icon, also as the mark at the head of the onboarding (D198); the hub's Muskelgruppen card put there whole when its history arrives, after the finding on the iPhone (D199); «Pläne verwalten» leading to the training plans from Heute and from Muskelgruppen, and Back closing every sheet without losing what was typed (D200). Built with `--base=/Momentum-preview/` and `VITE_MOMENTUM_DB=momentum-preview`.
- **What to check** is the short list "After the tidy-up" at the end of `docs/device-tests.md` in `Momentum-App`. **Remove the preview from the Home Screen and add it again first**: an app there keeps the icon it was added with. There is no backup with real data: import the file of the day you check from `docs/wp3/aufraeumen/` (`momentum-pruefdaten-aufraeumen-2026-11-18.json` on 18 November, and so on to the 21st) — files made by the live app itself, so the import is the update on that day; do the list's first two points before the import. The onboarding can be walked as a rehearsal: Bereiche → Einstellungen → «Einführung ansehen», a row only this preview has.
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
