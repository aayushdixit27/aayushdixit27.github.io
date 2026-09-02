# aayushdixit27.github.io

Personal site for Aayush Dixit — product at Votal.ai. Live at
**https://aayushdixit27.github.io**

A workbench in a dark room lit by one task lamp. Three objects sit in the pool of
light. Clicking one turns it over to reveal a riveted aluminium equipment plate
with fixed fields: MODEL / SERIAL / IN SERVICE / RATED FOR / FAULT FOUND / CAUSE /
ACTION / STILL OPEN.

> Nothing here was ordered assembled. Some of it is still in pieces.

The conceit is that every piece of work is an instrument with a fault report on the
back. Each plate names what the thing was rated for, what went wrong, why, what was
done, and what is *still open* — the last field being the point of the whole site.

## Running it

There is no build step. No frameworks, no npm, no dependencies.

```sh
python3 -m http.server 8000
# then open http://localhost:8000
```

Opening `index.html` from the filesystem also works, though some browsers block
`file://` for the Google Fonts request.

## Layout

| path | what it is |
|---|---|
| `index.html` | the entire site — markup, CSS and JS in one file |
| `old-index.html` | earlier Senso verification-receipt page, kept reachable |
| `.well-known/senso-receipt/` | published UCP verification receipts (JSON) |
| `checkpoint-example.json`, `ucp-extension-example.json` | UCP format examples |
| `CLAUDE.md` | briefing for Claude Code — see below |

Deployment is GitHub Pages from `main`. Pushing to `main` publishes.

## How `index.html` is organised

Top to bottom, in one file:

1. **Design tokens** — palette, type stacks, gutter.
2. **Hero** — the room, the bench, the objects, and the arrival sequence.
3. **Band scopes** — `.band` and `.band.light`, the two colour scopes every
   section below the hero reads from.
4. **Sections** — under testing (three case studies), the logbook, shipped,
   build with me.
5. **JS** — object and plate data, plate SVG generator, flip interaction,
   arrival sequence.

The hero bench is pure CSS and inline SVG. Objects carry a `--depth` from 0 (near
edge) to 1 (far edge), and their bottom offset, resting scale and shadow tightness
all derive from it, so the perspective stays consistent if anything moves.

## Accessibility

Contrast is measured, not eyeballed. Body text runs 6.9:1 on the dark ground and
10.4:1 on the light panels; interactive colour meets 4.5:1 on every ground it is
used on. Focus is always visible, Escape closes an opened object, and the arrival
sequence is skipped entirely under `prefers-reduced-motion`.

## Licence

Content and design © Aayush Dixit. The code is here to read.
