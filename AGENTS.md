# 项目级 Codex 工作规则

## 项目概况

- 项目名称：products-skills
- 项目类型：可发布 AI skill 包 / 插件元数据包
- 主要入口：`SKILL.md`
- 主要输出物：`SKILL.md`、阶段技能目录、`skill.json`、插件元数据、README

## 工作模式

- 默认轻量模式处理文案、元数据和小范围技能说明更新。
- 涉及技能名称、安装方式、插件元数据、发布版本、目录结构时使用严格模式。

## 维护原则

- 保持一套 canonical skill 包，不维护 Codex 和 Claude 两份重复镜像。
- 根目录 `SKILL.md` 是主路由；阶段技能只做单一职责。
- 新阶段必须有清晰触发条件、输出格式和验证方式。
- 产品链路必须保留 8 个包内阶段：brainstorming、autoplan、writing-plans、plan-eng-review、test-driven-development、qa、investigate、ship。
- 不要把 writing-plans 或 test-driven-development 降级成外部可选依赖。
- README 顶部必须保留安装方式和 why-this-exists 说明。

## 验证

发布前至少执行：

```powershell
npx skills add . --list --full-depth
npx skills add . -g -a codex claude-code -y --full-depth
npx skills list -g -a codex --json
npx skills list -g -a claude-code --json
```

只提交本仓库内文件，不提交本机安装目录、缓存或下载产物。
