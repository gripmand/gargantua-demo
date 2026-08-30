# GARGANTUA — commercial playbook

**This file is the operating memory.** Every scheduled Claude session starts with no
context except this repo. Read this file first; update it last. If a decision isn't
written down here, the next session doesn't know it happened.

---

## Status

| | |
|---|---|
| **Validation status** | `PAPER` — pre-registered, accruing signal, NOT built |
| **Opened** | 2026-08-30 |
| **Verdict due** | 2026-10-11 (6 weeks) |
| **Signups to date** | 0 (form not yet wired — see Blockers) |
| **Spend to date** | $0 |

The registry doctrine applies to the business itself. GARGANTUA-as-a-product is a
`PAPER` edge: pre-registered with a bar it has to clear by a date, or it gets `KILLED`.
No building the hosted product before the bar clears.

---

## Thesis

GARGANTUA already exists as a private single-tenant instrument on the tailnet, with a
public static demo at the repo root. The commercial question is not "can this be built"
— it's built — but "will options traders other than its author pay for it."

**The wedge:** journal + expectancy + alpha attribution, fed by the user's own broker CSV.

**The hook:** you made $500; $210 of it was just being long a rising market; your alpha
was $290. Almost no retail journal decomposes P&L against a beta benchmark over each
trade's own holding window. It's the number that answers "am I actually good at this,"
and traders who have been at it a few years feel the absence of it.

**Why this slice and not the whole instrument** — see Constraints. It is the only
module that needs no licensed market data and carries no investment-advice exposure.

---

## Hard constraints

These bound everything. Do not propose a plan that violates one.

**1. Market data licensing.** Personal use of a feed ≠ redistribution to paying users.
Showing customers quotes, IV, or expected moves requires a commercial vendor agreement
and, for real-time exchange data, exchange agreements and per-user reporting. Costs run
from a few hundred a month into the thousands.
→ *Consequence:* the read-through web, earnings pre-flight/aftermath, and THE EYE's IV
ranks are **out of v1**. The journal wedge works on the user's own fills plus daily
index closes, which is the cheapest data class there is.

**2. The investment-advice line.** Analyzing trades the user already made is software.
Telling them what to trade looks like investment advice and points at registration
(SEC/state RIA). The pre-trade gate and any signal-like surface must stay framed as the
user's own checklist applied to the user's own rules — never as a recommendation from us.
→ *Consequence:* disclaimer stays on every public page. Marketing copy never predicts
returns, never implies performance, never shows a track record as an inducement.

**3. Single-tenant today.** The app reads flat JSON over a private network. Multi-tenant
means auth, per-user isolation, CSV ingest, billing, and a real backend. That's the
build, and it doesn't start until the bar clears.

**4. Never publish the private book.** The repo already enforces this — the demo carries
example data only. Any commercial asset draws from the example book, and every figure
shown publicly is labelled illustrative. No real fills, ever.

---

## The bar

Six weeks from 2026-08-30. A **qualified** reservation is one where trades/month ≥ 5.

| Qualified reservations by 2026-10-11 | Verdict | Action |
|---|---|---|
| ≥ 150 | `VALIDATED` | Build the hosted wedge. Charge the cohort before writing the backend. |
| 60 – 149 | `MARGINAL` | Positioning is close but thin. Rewrite the page against what the free-text answers actually say, run 4 more weeks. |
| < 60 | `KILLED` | Don't build. GARGANTUA stays a private instrument, which is a fine outcome. |

**Why 150 and not 30.** A free email reservation converts to paid at roughly 5–15% cold.
150 qualified signups is maybe 15–25 payers ≈ $450–725/mo at $29. That's the *floor* of
worth-doing, not the target. Anything under 60 cannot get there and the honest read is
no demand at this price for this framing.

**The stronger test, if signups come fast:** switch the button from a free reservation to
a real $29 pre-order via Stripe Payment Link. Ten cards beat four hundred emails. Do this
the moment there's evidence rather than at the end of the window.

---

## Distribution

The product isn't the constraint; being found is. These audiences are hostile to
marketing and receptive to method. **Lead with the doctrine, not the product.**

The registry discipline — kill-test bar, MC placebo, effective N, killed-stays-killed —
is genuinely interesting content to this crowd, and almost nobody in retail writes it up.
A post explaining how you decide an edge is real, that happens to mention the tool at the
bottom, will outperform any post about the tool.

| Channel | Approach | Rules |
|---|---|---|
| r/options, r/thetagang | Long methodology post; tool mentioned once at the end | Read each sub's self-promo rule first. Getting banned costs the channel permanently. |
| FinTwit / X | Thread on alpha-vs-beta decomposition with the demo screenshot | Reply to people complaining about their journal. |
| Elite Trader, options Discords | Participate first, link later | Never lead with a link. |
| Hacker News | "Show HN" only if the build ships | Wrong crowd for the waitlist, right crowd for the build. |

Every link posted anywhere gets `?src=` — `?src=reddit-options`, `?src=fintwit`. The form
records it. Without it you learn that people signed up and never learn where to spend the
next hour.

---

## Blockers — these need a human, and only these

Claude cannot open accounts, accept terms, hold money, or spend it. Each of these is
yours; nothing downstream of them can move until they're done.

- [ ] **Wire the form.** Pick Buttondown (list you can send from later) or Formspree
      (faster). Paste the POST URL into `FORM_ENDPOINT` in `launch/index.html`.
      **Until this is done the page collects nothing and the whole test reads as zero demand.**
- [ ] **Analytics.** Plausible (~$9/mo) or self-host Umami. Needed to compute conversion
      rate — signups alone can't tell a positioning problem from a traffic problem.
- [ ] **Domain.** Optional but the GitHub Pages URL costs credibility on a paid product.
- [ ] **Stripe account** — only when moving to the pre-order test.
- [ ] **Post the first methodology piece.** Has to come from you; a Reddit account with
      no history posting about trading method is spam and reads as spam.

## Budget vs. the $200/mo ceiling

| Item | Now | On build |
|---|---|---|
| Form/email collector | $0 (free tier) | ~$9 |
| Analytics | $0–9 | $9 |
| Domain | ~$1/mo amortized | ~$1 |
| Hosting | $0 (GitHub Pages) | ~$20 (app + db) |
| Stripe | — | 2.9% + 30¢ |
| Index close data | — | ~$0–30 |
| **Total** | **~$10/mo** | **~$70/mo** |

Validation is nearly free. The $200 is headroom for a paid-traffic test if organic
stalls — but don't buy traffic before the page converts organic traffic, or you'll pay
to learn something the free channel would have told you.

---

## What Claude does on a scheduled session

1. Read this file. Read `ops/LOG.md`.
2. Pull signup counts and channel breakdown; update **Status** above.
3. Read the free-text answers. They are the highest-value input in the whole test —
   if three people name the same missing thing, that's the actual product.
4. Rewrite landing copy against real objections; ship it.
5. Check the bar. If a threshold has been crossed, say so plainly and stop for a decision.
6. Draft the next methodology post for human review. **Never post it.**
7. Append to `ops/LOG.md`: date, what changed, what the numbers were, what's next.

**Standing limits.** Never send email, post publicly, spend money, or contact a signup.
Never publish real trade data. Never soften the bar because the number came in low —
a moved goalpost is how a `KILLED` edge gets traded anyway.
