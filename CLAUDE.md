# Briefing

## Who and what

Aayush Dixit, AI product builder, Product Lead at Votal.ai. This repo is the
personal site, live at https://aayushdixit27.github.io. One file, `index.html`.

**Audience: recruiters and founders arriving from a resume link.** They scan for
ten seconds. Clarity beats cleverness, and the path to email matters more than any
flourish.

## Standing constraints

**The resume is the source of truth.** Nothing factual goes on the site that is not
on the current resume. Do not embellish or invent an event to make copy land. If
the resume changes, the site changes to match it.

**One file, no build step, no framework, no JavaScript.** The page must render
completely with scripts off.

**No phone number or street address on the site.** Email, LinkedIn and GitHub only.

**Design system.** Based on the Console theme from Hallmark (github.com/Nutlope/hallmark),
picked by hand. Graphite colorway only: the site is dark in every browser, by choice
(a light colorway was tried and dropped). Colors are tokens on `:root`. Host Grotesk for everything a person reads; Atkinson
Hyperlegible Mono only for measured values. Amber means something a person did
(the primary button, my call, awards); cool blue means something an instrument
measured (dates, readings). Never swap those meanings or add a third accent.
The signature is that claims are set as readings, drawn to scale from the resume's
own numbers (the ~92% panel, the figures in Built). A new figure must use real
resume numbers and stay to scale. No eyebrows, all-caps labels, stat-tile rows or
decorative motion. Every text color is at least 4.5:1; re-measure
after any token change.

## History

Until November 2026 the site was a "workbench under a lamp" concept with flip-over
equipment plates and a scroll-driven intro. It was replaced with a plain page
because it was slow to read and its facts had drifted from the resume. That
version is in git history (commit `b06a245`) if anything needs recovering. The
plain page was then redesigned on the Console theme the same month.

## Deploying

`main` is GitHub Pages; pushing publishes. Ask before pushing unless publishing was
explicitly requested. After a push, confirm the live URL serves the new build
(Pages takes about 20 to 40 seconds).
