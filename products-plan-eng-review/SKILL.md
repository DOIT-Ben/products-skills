---
name: products-plan-eng-review
description: "Use when products-skills needs an engineering review before implementation, covering architecture boundaries, data flow, dependencies, error handling, testability, and release risk."
triggers: [products engineering review, product engineering review, products plan eng review, product plan eng review]
---

# Products Engineering Review

Use this after the product direction and plan are clear but before risky
implementation starts.

## Entry Conditions

- The plan touches shared behavior, data flow, APIs, storage, auth, performance,
  or release-sensitive code.
- Multiple implementation approaches are possible.
- The user wants confidence that the plan is technically sound.

## Review Protocol

Check:

- Architecture boundary: the change belongs in the proposed layer/module.
- Data flow: inputs, outputs, persistence, and state transitions are clear.
- Dependencies: new or changed dependencies are necessary and bounded.
- Error handling: failures, empty states, retries, and recovery are addressed.
- Testability: the behavior can be verified without fragile manual-only checks.
- Release risk: rollout, rollback, and compatibility concerns are known.

## Output

- Stage: `products-plan-eng-review`.
- Recommendation: go or no-go.
- Architecture boundary check.
- Data flow and dependency check.
- Error handling and recovery check.
- Testability and verification check.
- Key risk: the highest-impact risk.
- Smallest correction: required change if no-go.
- Gate: `continue` or `revise`.
- Next: usually `products-test-driven-development` or plan revision.

## Gate Rules

- Use `continue` when the plan is technically coherent enough to implement.
- Use `revise` when architecture, data flow, dependency, error handling, or
  testability gaps could cause rework or unsafe delivery.
