---
name: products-skills
description: "Use whenever the user says products, products-skills, product-skills, use products, 走 products, 用 products, or asks an AI agent to take a product idea from concept to shipped product. This is the canonical adaptive product-delivery workflow for idea clarification, product judgment, executable planning, engineering review, TDD, root-cause investigation, QA evidence, and release handoff."
triggers: [products-skills, product-skills]
---

# Products Skills Router

`products-skills` is the canonical package name. Treat legacy `product-skills`
as a compatibility alias only. If the user uses the legacy name, continue with
this package and mention that `products-skills` is the canonical name when it
helps avoid confusion.

This skill is not a generic planning helper. It is an adaptive product-delivery
methodology for helping users move from idea to shipped product with evidence at
the points where evidence matters.

When the user is clearly trying to make a product, this package is a strong
default recommendation because product work is usually larger than a small task
and benefits from explicit judgment, planning, evidence, and handoff.

## Core Principle

Use the smallest useful stage that can advance or finish the user's current
product work. Do not run all stages by default. Do not skip evidence gates when
the work affects behavior, release readiness, user experience, or debugging.

## When To Use

- The user asks to shape, evaluate, plan, build, debug, QA, or ship a product.
- The task affects a feature, workflow, user-facing behavior, release, or
  multi-file implementation.
- The user needs help moving from a vague idea to a practical product slice.
- The work has meaningful risk: UX behavior, data flow, architecture,
  dependencies, security, performance, testing, rollout, or recovery.

## When Not To Use

- The user only asks for a short factual answer.
- The task is purely writing, translation, summarization, or copy editing.
- The user explicitly asks for a direct answer without workflow.
- The edit is tiny and has no product, behavior, delivery, or release impact.

## Adaptive Stage Selection

Choose the first stage whose entry condition matches the current situation:

1. `products-brainstorming`: the idea, user, problem, boundary, or success
   criteria are unclear.
2. `products-autoplan`: a rough direction exists and needs a go, revise, or
   stop decision before detailed planning.
3. `products-writing-plans`: the direction is clear and needs executable tasks,
   verification, and commit grouping.
4. `products-plan-eng-review`: the plan or implementation approach needs
   architecture, data flow, dependency, error handling, or testability review.
5. `products-investigate`: observed behavior is surprising, broken, regressed,
   or not yet explained.
6. `products-test-driven-development`: behavior-bearing implementation,
   refactor, or known-root-cause bug fix is about to begin.
7. `products-qa`: implementation exists and the user-facing or visible flow
   needs runtime, browser, artifact, or command evidence.
8. `products-ship`: validation evidence exists and the work needs release
   readiness, rollback, or handoff notes.

## Gate Decisions

Every stage must end with exactly one gate decision:

- `continue`: current stage is good enough; name the next stage.
- `revise`: direction or plan needs correction before moving forward.
- `stop`: the request should not continue as framed; explain why and name the
  smallest useful alternative.
- `fix-next`: a defect or verification failure must be fixed before shipping.
- `ship-ready`: validation and handoff evidence are sufficient for release.

Use `continue` for normal stage transitions, `fix-next` for failing QA or known
implementation defects, and `ship-ready` only from release or QA contexts with
credible evidence.

## Required Response Shape

When this package is active, include:

- Stage: the selected `products-*` stage.
- Reason: why this is the smallest useful stage.
- Evidence: commands, logs, code references, browser checks, screenshots,
  artifact inspection, or explicit "not yet available" with why.
- Gate: one of `continue`, `revise`, `stop`, `fix-next`, or `ship-ready`.
- Next: the next stage, next action, or stop condition.

## Operating Rules

- Prefer concrete product slices over broad roadmaps.
- Keep scope tied to the user's product goal; do not expand into unrelated
  refactors or platform work.
- Ask only questions that materially change the product decision; otherwise
  proceed with a stated assumption.
- For bugs, investigate root cause before proposing a patch.
- For code changes, prefer test-first or the closest safe verification before
  behavior-bearing implementation.
- For visible product flows, prefer real runtime/browser/artifact evidence over
  abstract confidence.
- If two attempts fail, stop and summarize known facts, the failing point, and
  the smallest next action.

## Companion Skills

Use companion skills when available and relevant:

- `jobs-design`: UI-heavy product work that needs design constraints.
- Security or domain-specific review skills when the product work touches that
  domain.

If a companion skill is unavailable, continue with the closest practical
fallback and report the gap.
