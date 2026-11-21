# Momentum — temporary preview

Built output only, for real-device visual QA of `Momentum-App` before a branch
is merged. No source, no history.

- Built from commit `e1c3440` (Momentum-App, branch `claude/momentum-seed-push-plans-v5s9gq`, from the default branch at `f42823f`): **the starter plans** (2026-11-21, D205). A device is given the two training plans Push A and Push B once — a new one before its introduction, which is unchanged and chooses nothing; a device that already holds data on its first load of this build, beside its own plans and with its data as it was. A plan deleted or renamed does not come back, and a backup import brings the file's plans and no others. Also in this build, since the last publish: the app icon with the owner's values (D203) and the first visit that offers no update (D204). Built with `--base=/Momentum-preview/` and `VITE_MOMENTUM_DB=momentum-preview`.
- **What to check:** Gym › Trainingspläne shows Push A and Push B once; delete one, close and open the preview, and it stays gone. To see a new device, clear this site's data in Safari first (or walk the onboarding as a rehearsal: Bereiche → Einstellungen → «Einführung ansehen», a row only this preview has — the rehearsal stores nothing).
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
