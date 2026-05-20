# products-skills

**人人都可以是产品经理。**

`products-skills` 是一套公开可复用的 AI 产品落地技能包。它帮助 AI agent
把一个想法从“感觉可以做”推进到“可以判断、可以拆解、可以验证、可以交付”。

它不是一套繁琐流程，也不是让 AI 多写几段计划文本。它的目标更简单：

- 先判断方向，不急着开工。
- 先拆小版本，不把想法做成大工程。
- 先确认根因，不用补丁掩盖问题。
- 先拿到证据，不靠感觉宣布完成。
- 最后交付时，留下验证、风险和回滚线索。

如果你经常让 AI 帮你做产品、功能、页面、工具、自动化或完整小应用，
`products-skills` 可以让 AI 不只是会执行，还会在关键节点帮你做产品判断。

## 为什么需要它

AI 很会写代码，但真实产品失败往往不是因为代码写不出来，而是因为这些动作被跳过了：

- 用户是谁、问题是什么、成功标准是什么，没有讲清楚。
- 方向还没判断，就直接进入实施。
- 任务太大，第一版无法验证。
- 架构、数据流、依赖和错误处理到后面才补。
- 测试只是事后补一补，没有证明原来的缺口。
- UI 或运行流程没有真实证据就说完成。
- bug 没查清根因就直接打补丁。
- 交付时没有风险、验证记录和回滚说明。

`products-skills` 把这些容易漏掉的产品动作拆成 1 个总路由和 8 个阶段技能。
AI 会根据当前任务选择最小有用阶段，而不是强迫每件事都走完整流程。

## 适合谁

- 你有一个产品点子，但不知道第一步该做什么。
- 你想判断一个需求值不值得继续。
- 你想让 AI 先评审、再规划、再实现。
- 你正在做功能、页面、工具、SaaS、插件或自动化流程。
- 你希望 bug 先查根因，而不是直接补丁。
- 你需要 QA、交付、风险和回滚说明。

## 你会得到什么

| 你想要的结果 | products-skills 怎么帮你 |
|---|---|
| 更快判断 | 先做产品价值、风险和范围判断 |
| 更小第一版 | 把模糊想法收敛成可验证切片 |
| 更稳实施 | 规划任务、评审工程边界、再进入实现 |
| 更少乱修 | bug 先查根因，再进入修复 |
| 更可信交付 | 用测试、运行、浏览器或可见流程证据支撑结论 |

## 快速安装

公开仓库安装：

```powershell
npx skills add DOIT-Ben/products-skills -g -a codex claude-code -y --full-depth
```

只安装到 Codex：

```powershell
npx skills add DOIT-Ben/products-skills -g -a codex -y --full-depth
```

只安装到 Claude Code：

```powershell
npx skills add DOIT-Ben/products-skills -g -a claude-code -y --full-depth
```

先查看会发现哪些 skills：

```powershell
npx skills add DOIT-Ben/products-skills --list --full-depth
```

安装后请重启 agent 会话，让技能列表刷新。

## 本地仓库安装

如果你已经 clone 了仓库，也可以在仓库根目录执行：

```powershell
npx skills add . -g -a codex claude-code -y --full-depth
```

`--full-depth` 很重要。这个包不只有根目录 `SKILL.md`，还包含 8 个阶段子技能。

## 怎么触发

正式名称是：

```text
products-skills
```

常用触发说法：

```text
product
products
product-skills
use products
用 products
走 products
```

`product-skills` 是旧名称兼容。推荐新对话里使用 `products-skills` 或 `products`。

## 使用示例

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
Product: 我想做一个习惯追踪小应用，帮我判断第一版该怎么做。
```

## 工作流

这个包包含 1 个总路由和 8 个阶段技能。

| 阶段 | Skill | 什么时候用 | 关口结论 |
|---|---|---|---|
| 1 | `products-brainstorming` | 想法、用户、问题或成功标准还不清楚 | `continue`, `revise`, `stop` |
| 2 | `products-autoplan` | 已有粗方向，需要判断值不值得继续 | `continue`, `revise`, `stop` |
| 3 | `products-writing-plans` | 方向清楚，需要可执行计划和验证项 | `continue`, `revise` |
| 4 | `products-plan-eng-review` | 实施前需要评审架构、数据流、依赖、错误处理、可测试性 | `continue`, `revise` |
| 5 | `products-investigate` | bug、回归、异常行为或根因不明的问题 | `continue`, `revise`, `fix-next`, `stop` |
| 6 | `products-test-driven-development` | 已知根因修复、功能实现、重构或行为变化 | `continue`, `revise`, `fix-next` |
| 7 | `products-qa` | 实现后需要验证 UI、浏览器、表单、导航、CLI 或运行流程 | `ship-ready`, `fix-next`, `revise` |
| 8 | `products-ship` | 验证完成后，需要发布、风险、回滚和交接说明 | `ship-ready`, `fix-next`, `stop` |

总路由不会强迫每个任务走完 8 个阶段。它会选择当前最小有用阶段。

特别规则：如果 bug 根因未知，先走 `products-investigate`，不要直接进入 TDD 或补丁。

## 关口结论是什么意思

| 结论 | 含义 |
|---|---|
| `continue` | 当前阶段足够好，可以进入下一个明确阶段 |
| `revise` | 方向、计划或实现还需要调整 |
| `stop` | 不建议按当前方式继续 |
| `fix-next` | 有问题需要先修复，再考虑交付 |
| `ship-ready` | 验证和交接证据足够，可以发布或交付 |

## 仓库结构

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
  products-investigate/
    SKILL.md
  products-test-driven-development/
    SKILL.md
  products-qa/
    SKILL.md
  products-ship/
    SKILL.md
```

## 发布前验证

维护者发布前建议执行：

```powershell
npx skills add . --list --full-depth
npx skills add . -g -a codex claude-code -y --full-depth
npx skills list -g -a codex --json
npx skills list -g -a claude-code --json
```

场景测试在 `evals/evals.json`，覆盖模糊想法、粗方向、实施计划、bug、QA、交付、
非产品短问答和旧名兼容。

## English Version

`products-skills` is a public AI skill package for moving product ideas from
concept to shipped work.

It gives an AI agent a lightweight but disciplined product-delivery path:
clarify the idea, judge whether it is worth doing, plan the smallest viable
slice, review engineering risk, investigate unclear bugs, implement with
evidence, verify the visible flow, and prepare release handoff.

The core promise is simple: help the agent make better product decisions instead
of only writing more code.

### Why It Exists

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

### Install

Install for Codex and Claude Code:

```powershell
npx skills add DOIT-Ben/products-skills -g -a codex claude-code -y --full-depth
```

List skills before installing:

```powershell
npx skills add DOIT-Ben/products-skills --list --full-depth
```

Restart your agent session after installation.

### Trigger Phrases

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

### Workflow

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

## License

MIT
