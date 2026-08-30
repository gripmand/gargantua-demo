# GARGANTUA — repo notes

## What this repo is

The **public static exhibit** of GARGANTUA, a private options-trading command center.
It is a built Vite/React PWA served from GitHub Pages. Two things live here:

- `/` — the exhibit. `index.html` + `assets/` (built bundle) + the `*.json` data layer.
- `/launch/` — the commercial landing page. See `ops/PLAYBOOK.md`.

**The source tree is not in this repo.** `assets/index-*.js` and `assets/index-*.css` are
build output with hashed names. Do not hand-edit them, and do not try to add app features
here — changes to the instrument happen in the source repo and arrive as a fresh build.
What *is* editable here: `index.html`, the JSON data files, `launch/`, `ops/`.

## The one rule that matters

**The private book never ships.** Everything public carries example data only — see the
`"EXHIBIT - a fabricated example journal, not a real record."` marker in `journal.json`
and the `(example)` labels throughout `attribution.json`. Real fills, real positions, and
real P&L stay on the tailnet. Any figure reproduced on a public page is labelled
illustrative. This is not negotiable and applies to marketing copy as hard as it applies
to the app.

## The data layer

Flat JSON read by the app at runtime. Rough shape:

| File | Holds |
|---|---|
| `edges.json` | The evidence registry. Every edge claim + dated verdict. |
| `journal.json` | Trade journal — entry conditions, grades, VIX, extension, MAE, lesson. |
| `attribution.json` | P&L split into beta (`cf`) and skill (`alpha`). |
| `lab.json` | Equity curve. |
| `readthrough.json` | Correlated-name web for earnings read-through. |
| `aftermath.json` | Earnings pre-flight / post-print state. |
| `calendar.json` | Macro calendar — OPEX, CPI, FOMC, NFP. |
| `snapshot.json` | Market snapshot (largest file). |

`edges.json` carries the project's doctrine in its own `doctrine` field, and it governs
how claims are made everywhere, including in commercial copy:

> A number not in this file is a rumor.

Statuses: `VALIDATED` · `MARGINAL` · `PAPER` · `THIN` · `NOT_VALIDATED` · `KILLED`.
A killed edge stays killed absent fundamentally new data.

## Gotchas

- **The service worker is dormant by design, not broken.** `sw.js`/`offline.html` are
  absent here and the registration is guarded on secure context. The long comment at the
  bottom of `index.html` explains the full reasoning — read it before "fixing" anything.
- **`.nojekyll` must stay.** GitHub Pages otherwise eats paths beginning with underscores.
- **Base path is `./`, not `/`.** The same bundle serves at the tailnet root and on the
  Pages subpath. Absolute paths break the Pages deploy. Keep `launch/` links relative.
- The iOS PWA meta tags in `index.html` are load-bearing and hard-won; the comments say
  which symptom each one fixes. Don't prune them as boilerplate.

## Commercial work

`ops/PLAYBOOK.md` is the operating memory — thesis, constraints, the validation bar, and
the standing limits on what may be done without a human. `ops/LOG.md` is append-only
session history. **Read both before commercial work; update `LOG.md` after.**

Standing limits, repeated here because they matter: never send email, post publicly,
spend money, or contact a signup. Never move the validation bar to make a result pass.

## Conventions

- No build step for anything in `launch/` — single self-contained HTML file, inline CSS
  and JS. It has to survive being served as a static asset with no toolchain.
- Comments here explain *why*, often at length, and frequently record a symptom that was
  actually observed. Match that register: a comment that only restates the code is noise.
