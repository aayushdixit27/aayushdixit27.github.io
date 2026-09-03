# Briefing

## Who and what

Aayush Dixit — product at Votal.ai (seed-stage enterprise AI agent platform),
evaluation advisor at Senso.ai. Builds agents, then builds the tests that decide
whether they ship.

This repo is his personal site, live at https://aayushdixit27.github.io. One file,
`index.html`, no build step. Structure and how to run it are in `README.md` — read
that rather than asking.

**Audience: recruiters and founders arriving from a resume link.** Not a creative
audience with patience to spare. This changes real decisions: shorter than its
references, nothing that looks broken on first paint, no cleverness that costs
clarity. The site's job is to convert mild interest into a conversation, so the
path to contact matters more than any single flourish.

**Where the work happens.** This repo is the project. Sessions have repeatedly
been started from `~/Downloads/Personal Site`, which holds the resume and the
original brief but is not the project and contains a stale `index_2.html`. The
resume there is the source of truth for facts; everything else there is history.

## Standing constraints — settled, not open

**One file. No build step, no frameworks, no npm.** Not a preference; the site is
deliberately readable end to end.

**The palette is locked.** Do not introduce colours.

```
room #0A0806   umber #2C2119   bench #4A3624 → #2E2116
lamplight #E8C08A   bone #D8CCBB   light panel #D2CBC2
```

**Bench geometry, the `--depth` model and the flip logic are correct.** They were
worked out carefully and are load-bearing for every object on the bench. Do not
touch them unless explicitly asked to.

**All-caps appears ONLY on equipment plates and section kickers.** Anything else in
all-caps is out of system.

**Nothing factual that is not in the resume or already in the file.** Do not
embellish, do not invent an incident to make a story land. If copy cannot be
written without inventing an event, say so and stop.

**The hero runs a scroll-driven arrival sequence.** Four beats on a 280svh sticky
container, which gives 180svh of travel. Invariants:

- Every sequence rule is scoped to `html.sequence`. The CSS default is the
  finished bench. An inline `<head>` script opts in before first paint; a
  dead-man switch drops the opt-in after 2.5s if the sequence code never runs.
- Skipped entirely on a deep link, under `prefers-reduced-motion`, on a repeat
  visit in the same session, and at ≤760px.
- Never `preventDefault` on wheel or touch. A trackpad flick must be able to blow
  straight through the whole thing.
- `#intro` may fade but must never move. The objects assemble around the line;
  that is the entire idea.

## The three mistakes that keep recurring here

Each has been caught more than once. They are the reason to look twice.

**1. JS must never SUPPLY the visible state.** The CSS default must render the
finished page; JS may only opt *into* enhancements by adding a class. Instances:
links shipped as `href="#"` and filled by JS; `.lit` added by JS so the tagline
was invisible without it; a mobile fade left at opacity 0 when its
`requestAnimationFrame` never ran. Ask of any change: *if this script throws or
never runs, what does the visitor see?*

**2. `#glow` is absolutely positioned and paints over static siblings.** Three
instances — `#intro`, `#hint`, `#card` — and every one presented identically, as
"the text is just gone" on narrow screens. Anything placed in `#scene` that is
not positioned will be swallowed regardless of DOM order. Give it
`position:relative;z-index:1`; and if it also carries `left`/`bottom` from a
desktop rule, neutralise those with `auto` or it will silently shift instead.

**3. Contrast is per-ground, and there are four grounds.** A colour that passes on
one fails on another. This is why there are three different oxides — correct, not
a mistake to tidy up.

| ground | value | interactive oxide |
|---|---|---|
| dark room | `#0A0806` | `#CE4D30` (4.50:1) |
| light panel | `#D2CBC2` | `#8E3521` (4.87:1) |
| light tile | `#DDD7CF` | `#8E3521` (5.48:1) |
| plate metal | `#948B80`–`#9E958A` | `#5F2214` (3.63:1) |

Body prose is already 6.92:1 on dark and 10.36:1 on light. Do not lighten it.
Colours live in tokens (`.band` / `.band.light`); a hardcoded hex inside a `.band`
rule is a bug.

**The nav scrim is coupled to the link height** and will break quietly. Links are
44px targets spanning 18–82% of nav height, so the scrim holds `#0A0806` opaque
to 86% to stay under them. Change nav padding or font size without re-measuring
that span and the links drift into the fade — unscrimmed over a light panel they
measure 1.02:1.

## Verifying visual work

Measure; do not eyeball. Compute contrast ratios and element rects in the page
rather than judging from an image. **But the browser tooling here is an unreliable
instrument, in ways that have produced three false diagnoses** — read
`.claude/rules/browser-verification.md` before trusting any reading from it.

## Open questions — dated 3 Sep 2026

*If today is well past that date, treat these as stale and check the file itself.*

**The Votal plate's CAUSE line.** "Evaluation that runs beside the release train
gets read when there is time and skipped when there is not" asserts a diagnosed
cause. It is the one plate line not lifted from the resume or prior copy, has
never been confirmed by Aayush, and sits awkwardly beside the Votal case study,
which was deliberately written *without* a discovery narrative because the resume
supports only one sentence about that suite. Ask before leaning on it.

**The arrival tween's 1.8s duration is unverified.** `requestAnimationFrame` does
not run in the automated browser tab, so only the fallback path has ever been
observed. Nobody has confirmed the real pacing feels right.

**The claim only appears during the desktop arrival.** "I build AI agents, then
build the tests…" lives on the opening card, so repeat visits, deep links and
reduced-motion users never see it; they get the governing line plus credentials.
Mobile has it permanently. Aayush was told and has not yet decided.
