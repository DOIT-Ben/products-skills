---
name: products-brainstorming
description: "Use when products-skills needs to turn a fuzzy idea into a buildable product direction by clarifying user, problem, success criteria, constraints, scope, and viable options."
triggers: [products brainstorming, product brainstorming, brainstorming for products, product brainstorm, 头脑风暴, 产品头脑风暴, 需求澄清]
---

# Products Brainstorming

Use this as the first stage when the request is fuzzy, creative, broad, or
under-specified. The goal is to turn a vague idea into a product direction that
can be judged and planned.

## Entry Conditions

- The target user or job is unclear.
- The problem is described as an idea, desire, or solution without boundaries.
- Success criteria, constraints, or scope are missing.
- Several product approaches are plausible and the user needs a recommendation.

## Work Protocol

1. Restate the product intent in one sentence.
2. Identify the target user and the job they need done.
3. Name the concrete problem, pain, or opportunity.
4. Define success criteria that can later be tested or inspected.
5. Surface constraints: technical, time, data, UX, compatibility, release, or
   business constraints.
6. Offer 2-3 product slices or solution options with trade-offs.
7. Recommend one direction and explain why it is the smallest useful slice.

## Output

- Stage: `products-brainstorming`.
- Recommendation: the most promising product direction.
- User/job: who it serves and what they need done.
- Problem: the concrete pain or opportunity.
- Success criteria: observable outcomes or checks.
- Constraints: known constraints and important assumptions.
- Options: 2-3 approaches with trade-offs.
- Gate: `continue`, `revise`, or `stop`.
- Next: usually `products-autoplan`, `products-writing-plans`, or stop.

## Gate Rules

- Use `continue` when the idea is clear enough to evaluate or plan.
- Use `revise` when a missing user, problem, constraint, or success criterion
  materially changes the direction.
- Use `stop` when the idea is unsafe, not product-relevant, or too vague to
  improve without user input.

Ask only questions that change the product decision. Prefer concrete options
over open-ended interviews.
