---
name: products-writing-plans
description: "Use when products-skills has a clarified product direction and needs a decision-complete implementation plan with scope, likely files, ordered tasks, verification checks, and commit grouping."
triggers: [products writing plans, product writing plans, writing-plans, implementation plan, 产品实施计划, 拆任务, 任务拆解]
---

# Products Writing Plans

Use this after a direction has passed brainstorming or autoplan and needs to be
turned into executable work.

## Entry Conditions

- The product goal and first slice are clear.
- Implementation has not started or needs to be reorganized.
- Another engineer or agent should be able to execute without rediscovering the
  product decision.

## Plan Protocol

1. Define the goal in one sentence.
2. State included and excluded scope.
3. Identify likely files, modules, commands, or surfaces to inspect or change.
4. Break work into ordered tasks, each with an action and validation check.
5. Put verification before behavior-bearing implementation where practical.
6. Group commits by coherent product or verification slices.

## Output

- Stage: `products-writing-plans`.
- Goal: one sentence.
- Scope: included work and explicit non-goals.
- File map: likely files, modules, or surfaces.
- Tasks: ordered, bite-sized steps with validation.
- Test plan: failing tests, checks, browser verification, or artifact inspection.
- Commit plan: suggested grouping and commit message style.
- Gate: `continue` or `revise`.
- Next: `products-plan-eng-review` for risky plans, otherwise
  `products-test-driven-development`.

## Gate Rules

- Use `continue` when the plan is executable and verifiable.
- Use `revise` when tasks are too broad, validation is vague, scope is unclear,
  or key files/interfaces are unknown.

Do not write placeholder tasks like "add tests" or "handle edge cases"; name
the behavior or risk to verify.
