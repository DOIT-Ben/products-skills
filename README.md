# products-skills

`products-skills` 是一套独立的产品开发工作流技能包，供 Codex、Claude Code 和其他 `SKILL.md` 兼容智能体使用。

它把一次产品开发协作拆成 8 个清晰阶段：

1. 头脑风暴：把想法、边界、成功标准聊清楚。
2. 自动方案检查：检查方案有没有漏洞、缺口和风险。
3. 任务拆解：把方案拆成能执行、能验证的任务。
4. 工程评审：看架构、边界、依赖、测试和风险。
5. 测试驱动开发：先写失败测试，再实现。
6. QA 验证：在真实浏览器或运行环境里验证页面和流程。
7. 根因调查：出问题先查根因，不乱打补丁。
8. 交付发布：处理提交、发布准备、风险说明和交接。

## 为什么需要它

AI 做产品开发时，常见问题不是“不会写代码”，而是：

- 需求还没聊清楚就开始实现。
- 方案没有经过风险检查。
- 任务拆得太大，执行时容易跑偏。
- 架构边界、数据流、错误处理没有提前想。
- 测试在实现后才补，无法证明测试真的抓得住问题。
- 改完没有真实浏览器或流程验证。
- 出 bug 后直接补丁，没找到根因。
- 最后交付时说不清改了什么、怎么验证、还能怎么回滚。

`products-skills` 的目标是把这些动作变成一条稳定链路。你可以让智能体“走 products”，它会按当前任务选择最小必要阶段，不为了流程而流程。

## 安装

推荐使用 Skills CLI 从仓库目录安装。必须带 `--full-depth`，这样才能发现主入口和 8 个阶段技能。

同时安装到 Codex 和 Claude Code：

```powershell
npx skills add . -g -a codex claude-code -y --full-depth
```

只安装到 Codex：

```powershell
npx skills add . -g -a codex -y --full-depth
```

只安装到 Claude Code：

```powershell
npx skills add . -g -a claude-code -y --full-depth
```

安装前查看仓库里有哪些技能：

```powershell
npx skills add . --list --full-depth
```

安装后重启你的智能体会话，让技能列表刷新。

## 本地开发安装

如果不在仓库根目录，可以把下面的 `<path-to-products-skills>` 换成你的本机仓库路径：

```powershell
npx skills add <path-to-products-skills> -g -a codex claude-code -y --full-depth
```

或者在仓库根目录执行：

```powershell
npx skills add . -g -a codex claude-code -y --full-depth
```

## 怎么使用

最常用的方式是直接让智能体走主入口：

```text
用 products-skills 帮我看这个功能需求，先判断怎么做。
```

```text
走 products，把这个方案拆成能执行的任务。
```

```text
用 products 看这个 bug，先查根因，不要直接补丁。
```

```text
用 products 做一轮 QA，验证这个页面流程。
```

也可以直接点名某个阶段：

```text
用 products-brainstorming 先帮我梳理这个想法。
```

```text
用 products-plan-eng-review 评审这个实现方案。
```

```text
用 products-test-driven-development 先写测试再实现。
```

## 8 个阶段

| 阶段 | 技能名 | 什么时候用 | 输出重点 |
|---|---|---|---|
| 1 | `products-brainstorming` | 想法还模糊，用户、边界、成功标准不清楚 | 推荐方向、用户目标、约束、成功标准、关键问题 |
| 2 | `products-autoplan` | 已有粗方向，需要检查是否值得继续 | go / revise / stop、缺口、风险、下一步 |
| 3 | `products-writing-plans` | 方向明确，需要拆成可执行任务 | 目标、范围、文件地图、任务、验证、提交计划 |
| 4 | `products-plan-eng-review` | 实现前需要工程视角评审 | 架构边界、数据流、依赖、错误处理、可测试性 |
| 5 | `products-test-driven-development` | 要实现功能、修 bug、重构或改行为 | 失败测试、RED/GREEN 命令、实现文件、剩余测试缺口 |
| 6 | `products-qa` | 改完后要验证页面、表单、导航或可见流程 | 测试流程、证据、错误、回归、ship/fix 建议 |
| 7 | `products-investigate` | 出现 bug、回归、异常表现 | 复现状态、证据、根因、最小修复、验证命令 |
| 8 | `products-ship` | 实现和验证完成，需要交付 | 变更摘要、测试证据、风险、回滚、发布或交接说明 |

主入口：

| 技能名 | 作用 |
|---|---|
| `products-skills` | 产品开发总路由。根据当前任务选择上面 8 个阶段中最合适的一个或几个。 |

## 适合什么任务

适合：

- 新功能从想法到实现。
- 已有功能的迭代和重构。
- Web 页面、表单、后台工具、SaaS 工作流。
- 需要先评审方案再动代码的任务。
- 需要真实验证和交付说明的任务。
- bug、回归、异常行为的根因调查。

不适合：

- 一句话问答。
- 纯翻译、纯总结、纯改文案。
- 完全不涉及产品、代码、流程或交付的任务。
- 用户明确要求直接回答、不走流程的场景。

## 手动安装

如果你的智能体不支持 Skills CLI，只要它支持 `SKILL.md` 目录结构，可以手动放到技能根目录：

```text
<skills-root>\products-skills\SKILL.md
<skills-root>\products-skills\products-brainstorming\SKILL.md
<skills-root>\products-skills\products-autoplan\SKILL.md
<skills-root>\products-skills\products-writing-plans\SKILL.md
<skills-root>\products-skills\products-plan-eng-review\SKILL.md
<skills-root>\products-skills\products-test-driven-development\SKILL.md
<skills-root>\products-skills\products-qa\SKILL.md
<skills-root>\products-skills\products-investigate\SKILL.md
<skills-root>\products-skills\products-ship\SKILL.md
```

复制到任意兼容 `SKILL.md` 的技能根目录：

```powershell
Copy-Item -Recurse . "<skills-root>\products-skills"
```

## 仓库结构

```text
products-skills\
  README.md
  LICENSE
  skill.json
  SKILL.md
  .codex-plugin\
    plugin.json
  .claude-plugin\
    plugin.json
    marketplace.json
  products-brainstorming\
    SKILL.md
  products-autoplan\
    SKILL.md
  products-writing-plans\
    SKILL.md
  products-plan-eng-review\
    SKILL.md
  products-test-driven-development\
    SKILL.md
  products-qa\
    SKILL.md
  products-investigate\
    SKILL.md
  products-ship\
    SKILL.md
```

## 元数据文件

仓库包含轻量元数据，方便不同智能体或插件系统索引：

- `skill.json`
- `.codex-plugin\plugin.json`
- `.claude-plugin\plugin.json`
- `.claude-plugin\marketplace.json`

这些文件只描述技能包，不复制技能内容。真正的技能入口是根目录 `SKILL.md` 和各阶段目录。

## 常见问题

### 为什么安装命令要带 `--full-depth`？

因为仓库根目录有主入口 `SKILL.md`，同时子目录里还有 8 个阶段技能。某些 Skills CLI 版本默认只发现根目录主入口；加 `--full-depth` 才会扫描全部子目录。

### `product-skills` 和 `products-skills` 是什么关系？

`products-skills` 是当前仓库和主技能名。`product-skills` 是旧称，主入口里保留了兼容触发词，方便旧习惯继续生效。

### 一定要完整走 8 个阶段吗？

不需要。主入口会选择当前最小必要阶段。比如一个 bug 可能直接进入 `products-investigate`，一个已完成改动可能直接进入 `products-qa` 或 `products-ship`。

### UI 设计任务怎么办？

如果你同时安装了 `jobs-design`，可以让智能体把 UI 任务和 `jobs-design` 搭配使用：

```text
用 products 规划这个页面功能，用 jobs-design 约束界面设计。
```

## 许可证

MIT
