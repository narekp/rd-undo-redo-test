# Exploratory Testing Areas: Remote Development: Undo/Redo

**Purpose:** Areas to exploratory test after executing the test cases  
**Timebox:** <20 minutes per area

---

## A) Network Problems
- **Slow connection typing** - Type during slow connection, check if undo/redo works normally, no steps lost
- **Multi-file changes with bad connection** - Rename/move files, check if all files update properly
- **Split editors after reconnect** - Undo in one split should show same change in the other one

## B) Multiple Windows
- **Right-split editor** - Undo/redo should work same as usual edit mode
- **Detached window** - Undo/redo should work same as main window

## C) Git Operations
- **Git changes + normal edits mixed** - Should not create extra lines or delete wrong lines
- **Merge conflict fixes** - Undo should not bring back old conflict text

## D) Text Files
- **Line endings** - Should stay same after undo/redo
- **Spaces at line ends** - Should stay same after undo/redo

## E) Menu Commands
- **Code menu** - Generate, Comment, Reformat should undo/redo cleanly
- **Edit menu** - Paste, Join Lines, Column Edit should undo/redo cleanly
- **Multiple commands together** - Combined commands should undo in logical order
