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

**Design system.** Colors are tokens on `:root`, redefined for dark mode. One
typeface (Schibsted Grotesk). One accent, the resume's navy. The large opening
statement is the only loud element. No stat tiles, cards, eyebrow labels,
all-caps labels or decorative motion. Measure contrast; body and muted text are
both above 7:1 in light and dark.

## History

Until November 2026 the site was a "workbench under a lamp" concept with flip-over
equipment plates and a scroll-driven intro. It was replaced with this plain page
because it was slow to read and its facts had drifted from the resume. That
version is in git history (commit `b06a245`) if anything needs recovering.

## Deploying

`main` is GitHub Pages; pushing publishes. Ask before pushing unless publishing was
explicitly requested. After a push, confirm the live URL serves the new build
(Pages takes about 20 to 40 seconds).
