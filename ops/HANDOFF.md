# Handoff prompt — carry this into a new session

Paste the block below into a fresh chat. It is written to stand alone: a new session
has none of this conversation's context.

---

I want to build a small online business that reliably makes **$1,000/month**, that you
can operate for me in scheduled sessions with me only doing the things you legally
can't — opening accounts, holding money, and posting under my own name.

**Start by pushing back on the plan below, hard, before you build anything.** A previous
session settled on it in about an hour and it has not been tested against anyone. I want
your honest read on whether it's the best route to $1,000/mo or whether something else
is. Don't be agreeable — if the plan is wrong, say so and say why.

## What I already have

`gripmand/gargantua-demo` is the public static exhibit of **GARGANTUA**, a private
options-trading command center I built for myself. It's a Vite/React PWA on GitHub Pages;
the source tree lives in a separate private repo, this one holds the built bundle plus a
flat-JSON data layer. Read `CLAUDE.md` and `ops/PLAYBOOK.md` in that repo first — they
have the full picture.

What the instrument does: an **edge registry** with real statistical discipline (kill-test
bar, Monte Carlo placebo, effective N, t-stat limits, and six verdict states from
VALIDATED to KILLED, where killed stays killed); a **trade journal** grading each entry's
conditions (trend quality, VIX, extension from the 200MA, MAE); **alpha attribution**
splitting P&L into market beta vs. actual skill; an **earnings read-through web** of
correlated names; **earnings pre-flight/aftermath**; a macro calendar; and a pre-trade gate.

I trade options. This came out of my own practice, not market research.

## The plan I want you to challenge

Sell the **journal + expectancy + alpha attribution** slice as micro-SaaS, fed by the
user's own broker CSV. Hook: *you made $500, but $210 was just being long a rising
market — your alpha was $290.* Validate with a landing page and a waitlist before
building the multi-tenant version. There's a landing page at `launch/` in an open draft
PR, priced $29 founding / $49 standard, with a bar of 150 qualified signups by
2026-10-11 or the idea is killed.

## Why $1,000/mo changes the math

- 35 customers at $29/mo, or
- 21 at $49, or
- **10 at $99**, or
- **2 B2B contracts at $500**

Ten customers I can name is a completely different problem from 350 strangers on a
waitlist. Specifically evaluate these alternatives against the $29 consumer plan:

1. **Price up.** A $99/mo serious-trader tier. Market Chameleon is $100+, Trade Ideas
   more — the ceiling is higher than $29.
2. **Sell B2B.** Prop firms (FTMO-style) and trading educators need per-student journals
   with real attribution, have budgets, and two contracts is the entire target.
3. **Productized service.** A paid one-off audit of someone's trading system using my
   registry method — no multi-tenant build at all.
4. **Something I haven't thought of.** Including "this specific thing won't work, here's
   a better use of the same skills."

Flag anything that would make me look like a trading-signals grifter. That's a
credibility trap I want to stay far away from.

## Hard constraints — don't propose a plan that breaks one

1. **Market data licensing.** Personal use of a feed is not redistribution to paying
   customers. Showing users quotes/IV/expected moves needs a commercial vendor agreement,
   and real-time exchange data needs exchange agreements and per-user reporting. This is
   why the journal slice (user's own fills + daily index closes) was picked over the
   read-through web and earnings modules.
2. **The investment-advice line.** Analyzing trades someone already made is software.
   Telling them what to trade points at RIA registration. Stay on the analysis side.
3. **It's single-tenant.** Flat JSON over a private tailnet. Multi-tenant means auth,
   per-user isolation, CSV ingest, billing, a real backend.
4. **The private book never ships.** Everything public uses example data only, and every
   public figure is labelled illustrative. Non-negotiable.

## What you can't do, so plan around it

You can't open accounts, accept terms of service, hold or spend money, send email, or
post publicly. Those are mine. You also start every scheduled session with no memory
except what's committed to the repo — so operating state has to live in git, not in a
conversation.

Assume ~$200/mo of budget and ~5 hrs/week of my time, most of it on things only a human
can do.

## What I want out of this session

1. Your honest verdict on the current plan, and the alternative you'd actually pick.
2. A recommendation with the arithmetic: price, how many customers, how they get found.
3. Then build the first real asset for whichever path we settle on — not a summary of
   options, an actual deliverable.
4. Tell me plainly what's blocked on me, and what the earliest possible signal is that
   this is or isn't working.

Push back where I'm wrong. I'd rather kill this in week one than spend six months on it.
