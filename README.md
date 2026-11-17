# aayushdixit27.github.io

Personal site for Aayush Dixit, AI product builder. Live at
**https://aayushdixit27.github.io**

One page that mirrors the resume: what I do, three proof points, experience,
things I built, education and skills, and how to reach me.

## Running it

There is no build step, no framework and no dependencies.

```sh
python3 -m http.server 8000
# then open http://localhost:8000
```

## Layout

| path | what it is |
|---|---|
| `index.html` | the whole site: markup and CSS in one file, no JavaScript |
| `old-index.html` | earlier Senso verification-receipt page, kept reachable |
| `.well-known/senso-receipt/` | published UCP verification receipts (JSON) |
| `checkpoint-example.json`, `ucp-extension-example.json` | UCP format examples |
| `CLAUDE.md` | briefing for Claude Code |

Deployment is GitHub Pages from `main`. Pushing to `main` publishes.

## License

Content and design © Aayush Dixit. The code is here to read.
