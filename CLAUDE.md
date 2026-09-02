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

## Standing constraints — these are settled, not open

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

## The two mistakes that keep recurring here

These have each been caught more than once. They are the reason to look twice.

**1. JS must never SUPPLY the visible state.** The CSS default must render the
finished page. JS may only opt *into* enhancements by adding a class. Past
instances: links shipped as `href="#"` and filled by JS; `.lit` added by JS so the
tagline was invisible without it; a mobile fade that left `#shelf` at opacity 0
when its `requestAnimationFrame` never ran. Ask of any change: *if this script
throws, what does the visitor see?*

**2. Contrast is per-ground, and there are four grounds.** A colour that passes on
one fails on another. This is why there are three different oxides — that is
correct, not a mistake to tidy up.

| ground | value | interactive oxide |
|---|---|---|
| dark room | `#0A0806` | `#CE4D30` (4.50:1) |
| light panel | `#D2CBC2` | `#8E3521` (4.87:1) |
| light tile | `#DDD7CF` | `#8E3521` (5.48:1) |
| plate metal | `#948B80`–`#9E958A` | `#5F2214` (3.63:1) |

Body prose is already 6.92:1 on dark and 10.36:1 on light. Do not lighten it.
Colours live in tokens (`.band` / `.band.light`); a hardcoded hex inside a `.band`
rule is a bug.

## Verifying visual work

Measure; do not eyeball. Compute contrast ratios and element rects in the page
rather than judging from an image. **But the browser tooling here is an unreliable
instrument** — see `.claude/rules/browser-verification.md` before trusting any
reading from it.

## Open question — dated 2 Sep 2026

*If today is well past that date, treat this as stale and check the file itself.*

The Votal object's plate carries a CAUSE line — "Evaluation that runs beside the
release train gets read when there is time and skipped when there is not" — that
asserts a diagnosed cause. It is the one plate line not lifted from the resume or
prior copy, it has never been confirmed by Aayush, and it sits awkwardly next to
the Votal case study, which was deliberately written *without* a discovery
narrative because the resume supports only one sentence about that suite. It
should probably be cut or rewritten. Ask before shipping copy that leans on it.
