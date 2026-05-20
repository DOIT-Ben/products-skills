---
name: products-test-driven-development
description: "Use when products-skills is about to implement a feature, known-root-cause bug fix, refactor, or behavior change and needs test-first discipline or an explicit safe substitute before changing behavior."
triggers: [products tdd, product tdd, test-driven-development, TDD, 测试驱动, 先写测试]
---

# Products Test-Driven Development

Use this before behavior-bearing implementation. The point is confidence: a
test or explicit verification check must prove the intended behavior is being
checked before the behavior is changed.

## Entry Conditions

- A feature, refactor, behavior change, or known-root-cause bug fix is about to
  be implemented.
- The expected behavior can be expressed as a test, contract, fixture, CLI check,
  browser check, or artifact inspection.
- There is enough product direction or investigation evidence to know what
  "correct" means.
- For unknown-root-cause bugs, use `products-investigate` first.

## Red-Green-Refactor

1. RED: write one minimal failing test or verification check for the desired
   behavior.
2. Verify RED: run the exact command and confirm the failure is expected.
3. GREEN: implement the smallest change that passes the check.
4. Verify GREEN: rerun the exact command and confirm it passes.
5. REFACTOR: clean up only after green, keeping checks passing.

## Allowed Substitute

If automated tests are not practical, state the substitute before implementation:

- exact manual/browser/runtime check,
- why an automated test is not practical now,
- what evidence will prove the behavior works,
- what follow-up test gap remains.

## Output

- Stage: `products-test-driven-development`.
- Behavior under test.
- Test or verification file/check and exact name.
- RED command and expected failure.
- Implementation files touched.
- GREEN command and passing result.
- Remaining gaps or follow-up tests.
- Gate: `continue`, `revise`, or `fix-next`.
- Next: usually `products-qa` or `products-ship`.

## Gate Rules

- Use `continue` when behavior passes the agreed test or substitute check.
- Use `revise` when the test does not actually check the intended behavior.
- Use `fix-next` when implementation still fails verification.

If the test passes immediately, rewrite it; it did not prove the missing
behavior. Bug fixes must include a regression check for the original symptom.
