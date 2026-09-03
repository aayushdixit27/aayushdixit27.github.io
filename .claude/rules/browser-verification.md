# Browser verification — trust the right instrument

Operating instructions for the Chrome tooling in this repo. A number is only as
good as the instrument that produced it; this one lies in specific, repeatable ways.

## What is unreliable

- **`requestAnimationFrame` does not run at all.** Zero ticks in 1.5s, and
  awaiting it froze the renderer hard enough to time out the CDP call. This is
  the worst one: anything rAF-driven appears broken when it is fine, and
  `scrollTo({behavior:"smooth"})` is a silent no-op for the same reason.
- **`getComputedStyle` reads go stale.** Values have come back as the pre-transition
  state minutes after the transition finished — reporting `opacity: 0` on elements
  that were visibly at full opacity in a screenshot taken the same second.
- **`scrollTo` does not emit scroll events.** Programmatic scrolling moves
  `scrollY` without firing `scroll`, so any scroll-driven code appears dead.
- **Synthetic `Tab` and other keys often go to browser chrome, not the page.**
  `document.activeElement` stays on `BODY` and no handler runs.
- **Screenshots taken immediately after an action capture mid-transition,** and
  sometimes an entirely blank frame mid-scroll.

## What to do instead

- **Screenshots are ground truth for appearance.** When a computed style and a
  screenshot disagree, the screenshot is right.
- **Drive scroll with real wheel events** (the scroll action), not `scrollTo`.
- **To test a keyboard handler, dispatch the event on the object the listener is
  bound to** (usually `window`), and say plainly that this bypasses focus routing.
- **Wait for transitions to finish before screenshotting** — the longest transition
  in the hero is 1.5s, so allow ~2.5s after a state change.
- **Test breakpoints with an iframe of the target width,** not by resizing the
  window; window resize does not reliably reflow this tab.
- **Verify "is this pre-existing?" against `git show HEAD:index.html`** served
  separately, before claiming a bug is or is not a regression. This has changed the
  answer more than once.

## Cost of getting this wrong

Three separate false diagnoses in one session came from trusting this tooling:
a scroll handler declared dead when it was fine, a nav declared invisible when
it was painting correctly, and native smooth scrolling declared broken when the
tab simply was not compositing. In each case the screenshot or a fresh load
would have given the right answer immediately.

## Deploying

`main` is GitHub Pages. **Pushing publishes immediately.** Commit freely; ask
before pushing unless the request to publish was explicit. After any push, confirm
the live URL actually serves the new build before reporting success — Pages takes
roughly 20–40 seconds.
