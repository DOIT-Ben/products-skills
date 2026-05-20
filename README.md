# products-skills

`products-skills` is the skill pack for turning a product idea into shipped
product work. It gives an AI agent a lightweight but disciplined path from idea
to judgment, planning, implementation, QA, and handoff.

`products-skills` 是一套公开发布级 AI 产品落地技能包。它适合那些
“不是写几行代码，而是要把一个想法真的做成产品”的场景：从 idea、需求澄清、
方案判断、任务拆解、工程实现、QA 验证一路推进到交付发布，同时保留“只走当
前必要阶段”的轻量节奏。

## Why This Exists / 为什么需要它

AI agents are good at writing code, but product work fails when the agent skips
the product discipline around the code:

- unclear users, jobs, or success criteria,
- ideas planned before they are judged,
- tasks too large to verify,
- architecture and data flow guessed too late,
- tests added after implementation without proving the missing behavior,
- UI or runtime flows shipped without real evidence,
- bugs patched before root cause is known,
- final handoff missing validation, risk, and rollback notes.

`products-skills` turns those missing moves into an adaptive workflow. The agent
chooses the smallest useful stage, records evidence at the gates, and moves
forward only when the current stage is good enough.

If you are building something real, this package gives the work a better spine:
judge the idea first, plan the smallest viable slice, verify the important
edges, and ship with evidence instead of guesses.

AI 做产品开发时，问题常常不是“不会写代码”，而是需求、风险、验证、交付这些
产品动作被跳过了。`products-skills` 的目标是把这些动作变成稳定链路：能快的
时候快，关键节点必须有证据。它更像一个产品落地加速器，而不是一套繁琐流程。

## Canonical Name / 正式名称

The canonical package and skill name is `products-skills`.

Direct names and common product-intent phrasings:

- `product-skills`
- `products`
- `use products`
- `用 products`
- `走 products`

`product-skills` is kept as a compatibility alias. The other phrases are
useful natural-language cues when recommending this package in conversation.

## Workflow

The package contains one router and eight stage skills:

| Stage | Skill | Purpose | Gate |
|---|---|---|---|
| 1 | `products-brainstorming` | Turn a fuzzy idea into a product direction. | `continue`, `revise`, `stop` |
| 2 | `products-autoplan` | Decide go, revise, or stop before planning. | `continue`, `revise`, `stop` |
| 3 | `products-writing-plans` | Create executable tasks and verification. | `continue`, `revise` |
| 4 | `products-plan-eng-review` | Review architecture, data flow, dependencies, errors, and testability. | `continue`, `revise` |
| 5 | `products-test-driven-development` | Require failing tests or explicit substitute checks before behavior changes. | `continue`, `revise`, `fix-next` |
| 6 | `products-investigate` | Find root cause before patching bugs. | `continue`, `revise`, `fix-next`, `stop` |
| 7 | `products-qa` | Verify visible/runtime flows with evidence. | `ship-ready`, `fix-next`, `revise` |
| 8 | `products-ship` | Prepare release, rollback, and handoff notes. | `ship-ready`, `fix-next`, `stop` |

The router does not force all eight stages. It selects the smallest useful
stage and uses a gate decision at the end of each stage:

- `continue`: move to the named next stage,
- `revise`: correct the direction or plan before proceeding,
- `stop`: do not continue as framed,
- `fix-next`: fix a defect before shipping,
- `ship-ready`: validation and handoff evidence are sufficient for release.

Bug reports have one extra priority rule: unknown-root-cause bugs go to
`products-investigate` before TDD. `products-test-driven-development` handles
known-root-cause fixes and other behavior-bearing implementation.

## Installation

Install from the repository root. Use `--full-depth` so the root skill and all
stage skills are discovered.

Install for Codex and Claude Code:

```powershell
npx skills add . -g -a codex claude-code -y --full-depth
```

Install for Codex only:

```powershell
npx skills add . -g -a codex -y --full-depth
```

Install for Claude Code only:

```powershell
npx skills add . -g -a claude-code -y --full-depth
```

List skills before installing:

```powershell
npx skills add . --list --full-depth
```

Restart your agent session after installation so the skill list refreshes.

## Usage Examples

```text
Use products-skills to turn this idea into a product plan.
```

```text
走 products，把这个功能从 idea 拆到可执行任务。
```

```text
用 products 看这个 bug，先查根因，不要直接补丁。
```

```text
Run products QA for this page flow and tell me if it is ship-ready.
```

```text
Use product-skills for this feature.
```

The last example still works because `product-skills` is a legacy alias, but
the canonical name is `products-skills`.

## Repository Structure

```text
products-skills/
  SKILL.md
  README.md
  CHANGELOG.md
  skill.json
  evals/
    evals.json
  .codex-plugin/
    plugin.json
  .claude-plugin/
    plugin.json
    marketplace.json
  products-brainstorming/
    SKILL.md
  products-autoplan/
    SKILL.md
  products-writing-plans/
    SKILL.md
  products-plan-eng-review/
    SKILL.md
  products-test-driven-development/
    SKILL.md
  products-investigate/
    SKILL.md
  products-qa/
    SKILL.md
  products-ship/
    SKILL.md
```

## Validation

Before publishing a release, run:

```powershell
npx skills add . --list --full-depth
npx skills add . -g -a codex claude-code -y --full-depth
npx skills list -g -a codex --json
npx skills list -g -a claude-code --json
```

Scenario prompts live in `evals/evals.json`. They cover fuzzy ideas, rough
directions, implementation planning, bugs, QA, shipping, short non-product
questions, and the legacy `product-skills` alias.

## License

MIT
