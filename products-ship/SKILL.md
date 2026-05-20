---
name: products-ship
description: "Use when products-skills has finished implementation and validation and needs release readiness, rollback notes, risk summary, changelog language, or handoff."
triggers: [products ship, product ship, products handoff, product handoff]
---

# Products Ship

Use this when implementation is complete and validation evidence exists.

## Entry Conditions

- The product change has been implemented.
- Tests, QA, or equivalent verification evidence exists.
- The user needs release readiness, rollout notes, rollback guidance, or handoff.

## Ship Protocol

1. Summarize the user-visible change.
2. List validation evidence with exact commands, checks, artifacts, or browser
   results.
3. Identify files, modules, or product surfaces touched.
4. State known risks and residual gaps.
5. Provide rollback, recovery, or handoff notes.
6. Recommend release readiness.

## Output

- Stage: `products-ship`.
- Change summary.
- Tests and QA performed.
- Files or modules touched.
- Known risks and residual gaps.
- Rollback or recovery note.
- Handoff or release note.
- Gate: `ship-ready`, `fix-next`, or `stop`.
- Next: release, fix next, or stop.

## Gate Rules

- Use `ship-ready` when validation evidence supports release.
- Use `fix-next` when known failures or unacceptable gaps remain.
- Use `stop` when the work should not ship as framed.
