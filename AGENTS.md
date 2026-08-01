# AGENTS.md

## Cursor Cloud specific instructions

This repository is **documentation-only** — a public case study for "The Six-Layer
Integration Audit". There is intentionally **no application source code, no package
manager manifest, no automated tests, no linter, and no build system** in this repo.
The README states explicitly that the audit primitive's source remains private.

What actually lives here:
- `README.md` — the case study. Its core visual content is a set of **Mermaid**
  diagrams embedded as ```` ```mermaid ```` fenced code blocks.
- `sample/*.md` — two anonymized sample deliverables (executive summary, maturity
  scorecard).
- `diagrams/six-layers.md` — notes on how the diagrams are authored/rendered.
- `LICENSE` — CC BY-NC-SA 4.0 (docs only).

### The only meaningful "dev/run/validate" workflow

There is no server or app to start. Development means editing Markdown and confirming
the Mermaid diagrams still render. GitHub renders the Mermaid blocks natively; to
validate them locally, render with `mermaid-cli` (no repo install needed — fetch it
on demand with `npx`):

```
# render every mermaid block in README.md to SVGs (validates all diagrams)
npx -y @mermaid-js/mermaid-cli@11 -i README.md -o /tmp/render/README.out.md -p pptr.json
```

**Non-obvious gotcha:** `mermaid-cli` drives headless Chromium via Puppeteer, which
fails in this sandbox unless Chromium is launched with `--no-sandbox`. Pass a
Puppeteer config file via `-p`, e.g. a `pptr.json` containing:

```
{"args":["--no-sandbox","--disable-setuid-sandbox"]}
```

A non-zero exit or a `✅`-less run from `mermaid-cli` means a diagram has invalid
Mermaid syntax — that is the closest thing this repo has to a failing "test".

Because there are no dependencies to install, the startup update script is a no-op
(just verifies Node is present). `node` + `npx` are all that's required.
