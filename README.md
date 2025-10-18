# Remote Development Undo/Redo Testing

**Goal**: Test undo/redo functionality in remote development (standalone PyCharm = expected behavior)

## Quick Navigation
- [Test Results and Findings](https://github.com/narekp/rd-undo-redo-test/blob/main/TEST_RESULTS.md)
- [All Test Cases](https://github.com/narekp/rd-undo-redo-test/blob/main/testCases.md) 
- [Exploratory Testing](https://github.com/narekp/rd-undo-redo-test/blob/main/exploratory_areas_undo_redo_rd.md)
- [All Issues Filed](https://github.com/narekp/rd-undo-redo-test/issues)

## Scope and Testing Depth

### Scope: Undo/Redo in Remote Development
- **Core Editor Operations**: Typing, deletion, selection
- **File and Project Operations**: Create, delete, move, rename files
- **Daily Development Workflows**: Debugging, refactoring, imports, templates
- **IDE Integration**: Multi-window, Git, network scenarios (exploratory)

### Depth
**Level 1 - Foundation** (TC-01 to TC-09)
- Basic typing, deletion, undo/redo flows
- This is the foundation that must work reliably

**Level 2 - Professional Workflows** (TC-10 to TC-21)  
- Real Python development scenarios used daily
- What actually impacts developer productivity and trust

**Level 3 - Edge Cases, RD-Specific** (Exploratory)
- Network conditions, reconnection, multi-window behavior
- Where Remote Development differences from standalone emerge

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

Using priorities (p1, p2, p3) instead of severity levels/labels to make triage more straightforward - answers one question: how soon should it be fixed?
- Issue must have exactly one priority label (p1 / p2 / p3).
- Issue must have at least one of bug or ui / ux.
## non-undo critical bugs
- Are logged as issues with the `non-undo` label (see the Issues tab).
