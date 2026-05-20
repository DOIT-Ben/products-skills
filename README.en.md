# products-skills

`products-skills` is a public AI skill package for moving product ideas from
concept to shipped work.

It gives an AI agent a lightweight but disciplined product-delivery path:
clarify the idea, judge whether it is worth doing, plan the smallest viable
slice, review engineering risk, investigate unclear bugs, implement with
evidence, verify the visible flow, and prepare release handoff.

The core promise is simple: help the agent make better product decisions instead
of only writing more code.

## Why It Exists

AI agents are good at implementation, but product work often fails because the
agent skips product discipline:

- unclear users, jobs, and success criteria,
- ideas planned before they are judged,
- tasks too large to verify,
- architecture and data flow reviewed too late,
- tests added after implementation without proving the missing behavior,
- UI or runtime flows shipped without concrete evidence,
- bugs patched before root cause is known,
- final handoff missing validation, risk, and rollback notes.

`products-skills` turns those missing moves into an adaptive workflow. The agent
chooses the smallest useful stage and records evidence where evidence matters.

## Install

Install for Codex and Claude Code:

```powershell
npx skills add DOIT-Ben/products-skills -g -a codex claude-code -y --full-depth
```

List skills before installing:

```powershell
npx skills add DOIT-Ben/products-skills --list --full-depth
```

Restart your agent session after installation.

## Trigger Phrases

```text
products-skills
product
products
product-skills
use products
用 products
走 products
```

`products-skills` is the canonical name. `product-skills` remains as a legacy
alias.

## Workflow

| Stage | Skill | Purpose | Gate |
|---|---|---|---|
| 1 | `products-brainstorming` | Turn a fuzzy idea into a product direction. | `continue`, `revise`, `stop` |
| 2 | `products-autoplan` | Decide go, revise, or stop before detailed planning. | `continue`, `revise`, `stop` |
| 3 | `products-writing-plans` | Create executable tasks and verification checks. | `continue`, `revise` |
| 4 | `products-plan-eng-review` | Review architecture, data flow, dependencies, errors, and testability. | `continue`, `revise` |
| 5 | `products-investigate` | Find root cause before patching unclear bugs. | `continue`, `revise`, `fix-next`, `stop` |
| 6 | `products-test-driven-development` | Require failing tests or explicit substitute checks before behavior changes. | `continue`, `revise`, `fix-next` |
| 7 | `products-qa` | Verify visible or runtime flows with evidence. | `ship-ready`, `fix-next`, `revise` |
| 8 | `products-ship` | Prepare release, rollback, and handoff notes. | `ship-ready`, `fix-next`, `stop` |

The router does not force every task through all eight stages. It selects the
smallest useful stage for the current product work.

Unknown-root-cause bugs should go to `products-investigate` before TDD.
