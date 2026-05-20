---
name: products-qa
description: "Use when products-skills needs runtime, browser, UI, form, navigation, CLI, artifact, or visible-flow verification after implementation, with concrete evidence and a ship/fix recommendation."
triggers: [products qa, product qa, qa for products, qa for product]
---

# Products QA

Use this after a product-facing change has been implemented or when the user
asks whether a visible flow works.

## Entry Conditions

- Implementation exists.
- The change affects UI, forms, navigation, user-visible behavior, CLI output,
  generated artifacts, or release-critical flow.
- The result needs evidence, not just code inspection.

## QA Protocol

1. Identify the flow, environment, and expected outcome.
2. Run the closest real check: browser, app runtime, CLI command, test command,
   generated artifact inspection, logs, or screenshot.
3. Check for visible regressions, runtime errors, console errors, broken links,
   invalid output, or failed assertions.
4. Record what was not verified.
5. Recommend ship or fix-next.

## Output

- Stage: `products-qa`.
- Tested flow and environment.
- Evidence: command output, browser check, screenshot path, logs, or artifact
  inspection.
- Regressions or console/runtime errors found.
- Known gaps not verified.
- Recommendation: ship or fix-next.
- Gate: `ship-ready`, `fix-next`, or `revise`.
- Next: `products-ship`, `products-test-driven-development`, or additional QA.

## Gate Rules

- Use `ship-ready` only when the critical flow passes and remaining gaps are
  acceptable.
- Use `fix-next` when a defect, regression, runtime error, or failed check must
  be fixed before shipping.
- Use `revise` when the QA target or environment is unclear.
