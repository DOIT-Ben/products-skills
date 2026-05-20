---
name: products-writing-plans
description: Use when `products-skills` has a clarified product direction or requirements and needs an executable implementation plan before code changes.
triggers: [products writing plans, product writing plans, writing-plans, implementation plan, 产品实施计划, 拆任务, 任务拆解]
---

# Products Writing Plans

Use this after brainstorming/autoplan has produced a direction worth building.
The output should be concrete enough that another agent can execute it without
re-discovering the project.

## Output

- Goal: one sentence describing what will be built or changed.
- Scope: included and excluded work.
- File map: exact files or modules likely to be created, modified, or checked.
- Tasks: bite-sized ordered steps with owner, action, and validation.
- Test plan: the failing tests or verification checks each task should use.
- Commit plan: suggested commit grouping and message type.

## Rules

- Prefer small tasks that produce testable progress.
- Include exact paths when the repo is available.
- Do not write placeholder steps such as "add tests" or "handle edge cases";
  name the specific behavior to test.
- Keep TDD visible: every behavior-bearing task should start with the test or
  closest safe verification check.
- End by naming the next stage: `products-plan-eng-review` or
  `products-test-driven-development`.
