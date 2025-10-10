# remote‑dev undo/redo parity (jetbrains gateway + gitpod)

**goal**: Test undo/redo functionality in remote development (undo/redo in standalone PyCharm can be considered the expected behavior).

<!--
## how to read this repo
- `/plan/ScopeMatrix.md` — what will be tested (scope) and how deep (L1/L2/L3 where L3 is the deepest)
- `/plan/TestPlan.md` — short plan: objective, envs, entry/exit, evidence
- `/cases/` — one markdown per test case
- `/summary/SummaryMatrix.md` — one-line status per test
- `/env/rd_env_snapshot.txt` — environment snapshot (server + controller)
-->

## Oracle policy
- **standalone pycharm** is the expected behavior. If RD differs and it’s not an explicitly documented exception, a bug needs be filed.

## Fallback
- if gitpod is flaky, **ssh** with gateway will be used. (will be documented in notes if applicable..)

## Time estimate
- planned effort: 

## Bug Priority Definitions and Issue Labels
    - Created a label for the UI / UX tickets - "ui / ux".
    - For the severities there are "p1", "p2", "p3" created, where:
    p1 (Critical): core functionality is blocked
    p2 (High): issue that impedes user flows and/or major UX friction
    p3 (Medium/Low): medium concerns or minor quirks or issues

Using priorities (p1, p2, p3) instead of severity levels/labels to make triage more straightforward - answers one question: how soon should it be fixed?
- Issue must have exactly one priority label (p1 / p2 / p3).
- Issue must have at least one of bug or ui / ux.
## non-undo critical bugs
- Are logged as issues with the `non-undo` label (see the Issues tab).
