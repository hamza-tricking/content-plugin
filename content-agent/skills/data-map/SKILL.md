---
name: data-map
description: Builds a visual data map of everything gathered about the creator: one local HTML page in the creator's language, with an Obsidian-like tree graph (each point linked to what is under it), popups with data and explanation side by side, tables, charts and a timeline. Run it BEFORE giving worked content examples, and again after big updates. Use when the user asks to see all their data, a map, a dashboard or a graph of their content.
---

# Data map (show the data before the examples)

Order: finish the phase → build or update the data map → let the user look at it → only then give worked examples (`examples` skill).

## Source of truth
Read every file the agent has produced (`dna/`, `vault/`, `vault/landscape/`, `strategy/`, `gaps.md`, `ledger.md`, `sources.md`). Use only numbers and facts that are in those files. Mark guesses as guesses and missing data as missing. Never store usernames of followers or commenters. Do not include phone numbers, emails or account IDs.

## Output
One self-contained file `dashboard/content-map.html` in the working folder (inline CSS and JS, no build step; a web font link is optional with a system fallback). Language and direction = the creator's language (`dir="rtl"` for Arabic).

## Structure (tree: every point under its parent)
Root (the creator) → branches, each with its own color, and leaves under them:
1. Identity / DNA: niche, vision, off-limits, resources (time, budget, volume), loved vs hated videos, writing voice.
2. Account data: overview per platform, per-video table (views, saves, shares, skip), best vs worst, hook analysis, duration and posting time, platform snapshot.
3. Audience: who they are (country, gender, age per platform), what they say (comment types), which videos bring followers.
4. Competitors: seed table, what works for them, new close accounts, other-platform side.
5. Niche and market: ranked gaps with status (verified / plausible / crowded).
6. Content health: strengths (with evidence), weaknesses (the weakest first, e.g. the hook), what data is still missing.
7. Strategy and goals: goal progress bars from the baseline, angle (overlap diagram), pattern portfolio (donut), hook rules, posting and call-to-action flow, learning plan, closed loop.
8. Timeline: phases done, current, and future dates (day 30, day 90).
9. Sources and tools: what works, what failed, paid credits spent.

## Page parts
- Header + KPI tiles (followers, medians, the weakest metric in red, the strongest in green, target, credits spent).
- The graph: radial tree, pan by drag, zoom by wheel and buttons, hover highlights the node with its ancestors and descendants, legend chips to dim branches, readable labels outside the leaves (for RTL, text-anchor end grows to the right).
- One separate glass section per branch with cards; each card shows its data (tables, bars, donuts, meters, flows, tags) and opens the popup.
- Popup for every point: title, path (root ← … ← point), explanation in the creator's language on one side, data on the other side, buttons to go to the parent and children. It must close on a click outside it (overlay), on Escape and with a close button; clicks inside do not close it.

## Design
Light theme, glass cards (semi-transparent white, backdrop blur, soft border and shadow, soft colored background blobs), clean sans-serif, shapes and charts more than text, color codes: green = confirmed strength, amber = hypothesis or guess, red = weakness. Works at phone width with no horizontal page scroll.

## Check before showing
Open it in a browser: no console errors, popup closes all three ways, nothing overflows at 375 px. Then tell the user the path and ask them to look before the examples. If a Drive connector is used, upload it with the end-of-session backup.
