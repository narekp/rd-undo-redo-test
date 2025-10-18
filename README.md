# remote‑dev undo/redo parity (jetbrains gateway + gitpod)

**goal**: Test undo/redo functionality in remote development (undo/redo in standalone PyCharm can be considered the expected behavior).

## Test Artifacts
- plan/TestPlan.md — objective, envs, entry/exit, evidence, notes, etc. 
- cases/ — one md per test case https://github.com/narekp/rd-undo-redo-test/blob/main/testCases.md
- summary/SummaryMatrix.md — one-line status per test

## Test Strategy and User Focus

**Testing Depth**: From basic operations to developer workflows
- **TC-01 to TC-09**: Core undo/redo functionality
- **TC-10 onwards**: Real developer scenarios (debugging, refactoring, imports, templates, etc.)

**User-Centric Design**: Test cases modeled after actual Python developer activities in PyCharm

## Test Environment
System and local IDE: PyCharm 2025.2.3 (#PY-252.26830.99), macOS 15.3.2, Apple M1 Pro
RD client: PyCharm 2025.1.1.1 (#JBC-251.25410.159)
RD backend: Ubuntu 22.04.2 LTS, Linux 6.1.139, Python 3.8.16 (Gitpod container)

## Remote Dev target (current)
**Date change:** 2025-10-16
**Why the switch:** *Why:** Gitpod Classic sunset; Ona works for me after installing JetBrains Toolbox and starting a PyCharm trial.
- OS: Ubuntu 24.04.3 LTS
- Kernel: `6.14.10-gitpod`
- User/Host: `vscode` on a cloud host

**Fallback (for reference):** Gateway > SSH > local Docker (Ubuntu 22.04)  
Purpose: contingency only - validated and working (executing on Ona)

## Oracle policy
- **standalone pycharm** is the expected behavior. If RD differs and it’s not an explicitly documented exception, a bug needs to be filed.

## Fallback
- If gitpod is flaky, **ssh** with gateway will be used. (will be documented in notes if applicable..)

## Time estimate and Delivery
- planned effort: ~16 hours
- planned delivery: Tuesday, Oct 14

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
