# Momentum — temporary preview

Built output only, for real-device visual QA of `Momentum-App` branch
`claude/momentum-wp3` before it is merged. No source, no history.

- Built from commit `6806630` (Momentum-App, branch `claude/hopeful-carson-4utktp`, WP3 block 7E at STOP 7E-b, on 2026-11-17: the onboarding in direction C with the owner's answers at STOP 7E-a2 — the flat ground, the first slide's picture with its example values, the Gym card with the body's still, the Rookie stage, the areas as two tiles, one card per question category, the weekly targets as two rows of seven, the summary as tiles — in the app's system font; Mind opens with three starter questions, one per category, and «Weiter» waits with «Wähl mindestens eine Frage oder nimm Mind ab.» while none is chosen. It is built on block 7D as the owner accepted it, `claude/momentum-wp3` at `3e153fa` merged in, and carries everything of that build) with `--base=/Momentum-preview/` and `VITE_MOMENTUM_DB=momentum-preview`.
- **For the check of block 7E** the owner sees the onboarding twice: **on a new device** — this preview in a private tab, or with its data cleared — where it is the first thing the app shows; and **as a rehearsal on a device with data**: Bereiche → Einstellungen → «Einführung ansehen», a row only this preview has. The rehearsal walks the flow as a new device does and writes nothing; «Starten» at its end, Back at any step, or a reload return to the app. For data to rehearse on, import the file of the check day from `docs/wp3/stage7d/` in `Momentum-App` (`momentum-pruefdaten-7d-2026-11-17.json` on 17 November, `…-2026-11-18.json` on the 18th). There is no backup with real data.
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
