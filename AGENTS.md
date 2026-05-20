# Project Rules for Codex

## Project Overview

- Project name: `products-skills`
- Project type: public AI skill package and plugin metadata package
- Canonical skill entry: `SKILL.md`
- Canonical package name: `products-skills`
- Legacy alias: `product-skills`
- Main deliverables: root router skill, eight stage skills, metadata, README,
  changelog, and eval prompts

## Working Mode

- Use lightweight edits for wording, metadata, examples, and documentation.
- Use stricter review when changing skill names, triggers, install paths,
  versioning, stage count, or release metadata.

## Maintenance Principles

- Maintain one canonical package; do not create separate Codex and Claude
  mirrors.
- Keep `products-skills` as the only canonical name.
- Preserve `product-skills`, `products`, `用 products`, and `走 products` as
  compatibility aliases.
- Keep the root `SKILL.md` as the router.
- Keep stage skills single-purpose and evidence-oriented.
- Preserve the eight stage model: brainstorming, autoplan, writing-plans,
  plan-eng-review, test-driven-development, investigate, qa, and ship.
- Use adaptive gates instead of forcing every task through all eight stages.
- Do not weaken evidence requirements for TDD, investigation, QA, or shipping.

## Verification

Before publishing, run:

```powershell
npx skills add . --list --full-depth
npx skills add . -g -a codex claude-code -y --full-depth
npx skills list -g -a codex --json
npx skills list -g -a claude-code --json
```

Review `evals/evals.json` when trigger behavior or stage routing changes.

Only commit files in this repository. Do not commit local install directories,
caches, generated workspaces, or downloaded artifacts.
