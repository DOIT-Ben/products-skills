---
name: products-test-driven-development
description: Use when `products-skills` is about to implement a feature, bugfix, refactor, or behavior change and needs test-first discipline.
triggers: [products tdd, product tdd, test-driven-development, TDD, 测试驱动, 先写测试]
---

# Products Test-Driven Development

Use this before changing behavior. The point is confidence: a test that fails
first proves the intended behavior is actually being checked.

## Red-Green-Refactor

1. RED: write one minimal failing test for the desired behavior.
2. Verify RED: run the exact command and confirm the failure is expected.
3. GREEN: implement the smallest change that passes the test.
4. Verify GREEN: rerun the exact command and confirm it passes.
5. REFACTOR: clean up only after green, keeping tests passing.

## Output

- Behavior under test.
- Test file and exact test name.
- RED command and expected failure.
- Implementation files touched.
- GREEN command and passing result.
- Remaining gaps or follow-up tests.

## Rules

- No behavior-bearing implementation before a failing test or explicit user-approved substitute.
- If the test passes immediately, rewrite it; it did not prove the missing behavior.
- If the test fails for setup or typo reasons, fix the test until it fails for the right reason.
- Do not broaden scope during GREEN.
- Bug fixes must include a regression test for the original symptom.
