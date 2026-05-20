---
name: products-skills
description: Use when the user says products, products-skills, product-skills, or asks for a structured product delivery workflow across brainstorming, autoplan, writing plans, engineering review, TDD, QA, investigation, or shipping.
triggers: [products, products-skills, product-skills, use products, 走 products, 用 products, product workflow, product delivery workflow, brainstorming, 头脑风暴, writing-plans, test-driven-development, TDD]
---

# Products Skills Router

Use the smallest stage that can finish the user's current product work. Treat
`products`, `products-skills`, and legacy `product-skills` as the same workflow.

This package is a product-delivery router. It is not a ceremony generator. Pick
one stage, do real work, verify it, then move to the next stage only when needed.

## When To Use

- The task affects a feature, workflow, user-facing behavior, release, or multi-file implementation.
- The user asks to brainstorm, clarify, plan, build, debug, review, QA, or ship a product change.
- The task requires choosing between multiple implementation approaches.
- The task has meaningful risk: data changes, UI behavior, architecture, dependencies, security, performance, or release impact.

## When Not To Use

- The user only asks for a short explanation.
- The task is a tiny one-off edit with no behavior change.
- The user explicitly asks for a direct answer without workflow.
- The task is purely writing, translation, or summarization.

## Bundled Stages

- `products-brainstorming`: clarify the idea, boundaries, users, and success criteria.
- `products-autoplan`: automatically inspect the proposed direction for gaps, risks, and missing requirements.
- `products-writing-plans`: split an approved direction into executable tasks.
- `products-plan-eng-review`: review architecture, boundaries, dependencies, error handling, and engineering risk.
- `products-test-driven-development`: write failing tests before behavior-bearing implementation.
- `products-qa`: verify pages, forms, navigation, and visible flows in a real browser or equivalent runtime.
- `products-investigate`: find root cause before patching bugs or regressions.
- `products-ship`: handle commit, release readiness, rollback notes, and delivery handoff.

## Companion Skills

Use these if they are available in the current agent runtime:

- `jobs-design`: UI-heavy work needs product-focused frontend constraints.

If a companion skill is unavailable, continue with the closest practical fallback:
clarify the goal, write a compact plan, add verification before changing behavior,
and report evidence.

## Operating Rules

- Start with a recommendation and the reason.
- Keep scope to the user's product goal; do not expand into unrelated refactors.
- Prefer real commands, tests, logs, browser checks, parser checks, and direct artifact inspection over abstract confidence.
- If two attempts fail, stop and summarize known facts, the failing point, and the smallest next action.
- Report changed files, verification evidence, risks, and the next handoff step when work is complete.
