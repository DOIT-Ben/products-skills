---
name: products-autoplan
description: "Use when products-skills has a rough direction and needs a product judgment gate before detailed planning: go, revise, or stop based on value, scope, risk, evidence, and delivery feasibility."
triggers: [products autoplan, product autoplan, autoplan for products, autoplan for product]
---

# Products Autoplan

Use this before detailed planning when a direction exists but still needs a
product-quality decision.

## Entry Conditions

- A candidate product direction or feature slice exists.
- The user wants to know whether it is worth building.
- The idea may have missing requirements, unclear value, risky scope, or weak
  validation.

## Review Rubric

Check:

- User value: the user, job, and benefit are clear enough.
- Scope: the first releasable slice is small enough to implement and verify.
- Requirements: critical behavior, constraints, and non-goals are known.
- Delivery risk: dependencies, data, UX, security, or release risks are visible.
- Verification: there is a practical way to prove the result works.

## Output

- Stage: `products-autoplan`.
- Recommendation: `go`, `revise`, or `stop`.
- Why: the main reason for that call.
- Missing requirements: only requirements that affect the decision.
- Risks: overengineering, delivery, UX, release, or validation risks.
- Smallest next action: the next concrete step.
- Gate: `continue`, `revise`, or `stop`.
- Next: usually `products-writing-plans`, `products-brainstorming`, or stop.

## Gate Rules

- Use `continue` only when the first product slice is clear enough to plan.
- Use `revise` when the direction is promising but needs narrower scope,
  missing requirements, or risk reduction.
- Use `stop` when value is unclear, feasibility is poor, or the request should
  not continue as framed.
