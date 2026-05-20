---
name: products-investigate
description: "Use when products-skills hits a bug, regression, surprising behavior, failing test, or unclear runtime issue and needs root cause before patching."
triggers: [products investigate, product investigate, products debugging, product debugging]
---

# Products Investigate

Use this before changing code when behavior is surprising, broken, regressed, or
not yet explained.

## Entry Conditions

- A bug, regression, failing test, runtime error, or unexpected behavior exists.
- The cause is not known.
- A patch would be guesswork without reproduction or evidence.

## Investigation Protocol

1. Reproduce or narrow the trigger.
2. Collect evidence: logs, errors, tests, browser state, data, recent changes,
   configuration, or relevant code.
3. Separate symptoms from cause.
4. State the root cause as specifically as the evidence allows.
5. Propose the minimal fix path and the validation check that proves it.

## Output

- Stage: `products-investigate`.
- Reproduction status or narrowed trigger.
- Evidence inspected.
- Root cause.
- Minimal fix path.
- Validation command or check.
- Gate: `continue`, `revise`, `fix-next`, or `stop`.
- Next: usually `products-test-driven-development` or stop.

## Gate Rules

- Use `continue` when root cause is clear enough to write a regression check or
  minimal fix.
- Use `revise` when more evidence is needed before implementation.
- Use `fix-next` when a defect is confirmed and must be fixed.
- Use `stop` when the issue cannot be reproduced and no useful next check
  remains.
