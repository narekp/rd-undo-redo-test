## P1-01

**Verify that undo/redo strictly follows last-in-first-out (LIFO)**

1. In any editable file, type three characters one by one (e.g., `A` then `B` then `C`)
2. Do **undo (cmd+z)** three times

   **Expected:** removes `C`, then `B`, then `A` (in that order)
   
3. Do **redo (cmd+shift+z)** three times.

   **Expected:** replays `A`, then `B`, then `C` in order

---

## P1-02

**Verify that rapid sequence of Undo/redo Does Not skip or corrupt steps.**

1. Type or paste a short token (e.g., `X`) 20 times on new lines.
2. Perform **undo (cmd+z)** quickly N times

   **Expected:** exactly N tokens are removed.

3. Perform redo the same number of times (N)

   **Expected:** exactly N tokens reappear, counts match.

---

## P1-03

**Verify that a new edit clears the redo stack**

1. Type a word `HEL` then paste the word `LO` to make `HELLO`
2. Undo (expected = `HEL`)
3. Redo (expeced = `HELLO`) 
4. Undo again (expected = `HEL`)
5. Type `!` to make `HEL!`
6. Do redo.
   
   **Expected:** nothing happens, Redo stack is empty as it is cleared by the new edit (`!`).

---

## P1-04

**Verify that undo/redo is applies properly to multi-caret changes in a single step**

1. Create multiple carets by adding carets to selected lines (hold the `option` key and click on the selected lines' places)
2. Type a token `ABC` once.
   
   **Expected:** all carets insert simultaneously.

4. Do undo

   **Expected:** All `ABC `insertions revert together simultaneously at the same positions.
   
5. Do redo
   
   **Expected:** All `ABC `insertions reapply together simultaneously at the same positions.

---

## P1-05

**Verify that editing in one split reflects in the other and shares history.**

1. Open the **same file** in right/left split (two panes) (right click the file > "Open in Right Split")
2. Type `X` pane A

 **Expected:** `X`is typed in pane B on identical location (both panes mirror each other)
   
3. On pane B do Undo.
   
   **Expected:** the change (`X`) is undone in both panes simultaneously and both panes show the same state.
   
4. Do redo.
   
   **Expected:** the change (`X`) appears back in both panes.

---

## P1-06

**Verify that file/module rename undo/redo adjusts and reverts imports properly**

1. Rename `file_a.py` (where `file_b.py` imports it)
2. Change the name to `file_c`
   - Verify an import error appears in `file_b`
4. Undo

The original filename (`file_a.py`) and all import statements are reverted; the import error in `file_b`is cleared.

5. Redo

**Expected Result:** The filename changes back to `file_c.py` with imports updated again

---

## P1-07

**Verify that moving a file updates imports and is reversible**

1. Move a file to a different folder using the IDE move/refactor.

**Expected:** the file where the code was imported updates automatically, no unresolved imports.

2. Do **undo**.
   
   **Expected:** file returns to original location; imports revert.
   
4. Redo

   **Expected:** move and import updates apply again properly.

---

## P1-08

**Verify that file deletion undo/redo removes and restores content properly**

1. Right click on a folder > New > File.
2. Name the new file `test_deletion.txt` > Enter.
3. Type `test content` into the file and save.
4. Right click `test_deletion.txt` > Delete > OK (uncheck Safe delete > OK).
- Make sure `test_deletion.txt` is deleted.
5. Undo

  **Expected:** `test_deletion.txt` reappers in the same directory and has `test content` in its body.

6. Redo

**Expected Result:**

**Expected:** `test_deletion.txt` is deleted again.

---

## P1-09

**Verify that Safe Delete undo/redo removes and restores usages properly**

1. In a directory (marked as Source Root; to enable import auto resolution) create two files:
a. file1.py
b. file2.py
2. In file1.py add `def test_safe_delete(): return "hello"`
3. In file2.py add `from file1 import test_safe_delete` and `result = test_safe_delete()`
4. Right click on `file1` > Delete (make sure `Safe Delete`is checked) > OK > Press "Refactor Anyway"
   - Make sure `file1` is deleted and that `file2` has unresolved reference errors on `from test1 import test_safe_delete`
6. On Project panel perform Undo

   **Expected:**
   - `file1` is restored to its directroy and has `def test_safe_delete(): return "hello"`
   - in `file2` function and usage are restored without errors.
  
7. Perform Redo

   **Expected:**
   - `file1` is removed again
   - `file2` has unresolved reference errors due to usage being removed again.
   
---

## P1-10

**Verify that rapid typing/deleting is properly undoable**

1. Type `testing` in a file
2. Press "Backspace" 3 times (result = `test`)
3. Undo
   
 **Expected:** `testing` returns completely

4. Redo

 **Expected:** Back to `test`
 
---

## P1-11

**Verify that undo/redo history affect only the current/selected document**

1. Open two different files (A and B).
2. Make one edit in each add text `test` in each
4. Perform Undo in `file B`
   
   **Expected:** `test` is removed from `File B`, `file A` stays unchanged.
   
5. In file A do Undo
   
   **Expected:** `test` is removed from `File A`, `file B` stays unchanged.

6. In File A do Redo

   **Expected:** File A now has `test` again and File B still has no `test` in its body.
   
---

## P1-12

**Verify Undo behavior when Remote Session connection is disconnected and post-reconnection**

1. Make an edit in File A, add text `import`
2. Disconnect the internet (e.g. toggle Wi-Fi off) so that the remote session lost connection.
3. Undo
   
   **Expected:** No change occurs, undo doesn't affect, `import` stays as is
   
4. Reconnect > remote session restored
   
   **Expected:** editor is in a consistent state matching the state before the remote connection was lost
   
5. in File A do Undo

   **Expected:** `import` is removed.

---

## P1-13

**Verify that Undo/Redo functions properly for bulk replace across multiple files and remains atomic**

1. Make sure a token appears across several files (`test_placeholder`).
2. Run a "Replace in Path" (cmd+shift+r/ctrl+shift+r) to replace `test_placeholder` with `bulk_updated_placeholder` in multiple files at once ("Replace All")
- Make sure all the ocurrences are changed to `bulk_updated_placeholder`
3. Undo

  **Expected:** All newly updated `bulk_updated_placeholder` tokens are reverted back to `test_placeholder`.

4. Redo

  **Expected:** The same set of files is updated again to `bulk_updated_placeholder`. 

---

## P1-14

**Verify Undo/Redo functions properly in steps when doing big grouped**

1. Create a `x.py` file with 10-line code block
2. Select the block and copy to the clipboard
3. Paste 9 times starting from row 11
- make sure the block is pasted properly and ends on line 100
4. Perform Undo three times

   **Expected:** the last 3 duplicated blocks are removed (each block disappears with a single step), editor remains responsive (no freeze/stall), ends on row 70.

5. Perform Redo twice

   **Expected:** Two blocks are restored back and ends on line 90

---

## P1-15

**Verify redo works correctly after a disconnect/reconnect**

1. Make an edit in a file
2. Undo
3. Disconnect the internet so that remote session connection is lost
4. Reconnect the internet
5. Redo

   **Expected:** the undone change returns correctly - no errors, no divergence.

---

## P1-16

**Verify that a Quick Fix import is fully removed/returned by undo/redo**

1. In any Python file, write a call to a function that isn’t imported yet (e.g., `ping()`).
2. Place caret on the unresolved call and press (option+enter / alt+enter) > "intention actions" choose an appropriate **Import …** intention.
- appropriate import is done in code and the error is gone
3. Undo

   **Expected:** the added import is removed, code returns to the unresolved state exactly.

4. Do Redo.

   **Expected:** the same import is added back exactly (same location in code).

---

## P1-17

**Verify that editing a line during debug can be undone/redone without side effects**

1. Open any runnable Python script and start Debug (click the green bug icon on header)
2. Toggle a breakpoint on a line
3. On that same line, type a small change (e.g., append a short comment).
4. Do undo

   **Expected:** the change disappears, breakpoint remains, session is stable.

5. Do redo

   **Expected:** the change returns, breakpoint remains unchanged.

---

## P1-18

**Verify that reformatting is a single reversible Undo step**

1. In any Python file, deliberately mess spacing/indent/blank lines.
2. Run **Reformat Code** (option+cmd+l / alt+cmd+l).
- make sure the IDE adjusts the formatting based on the based on the active code style scheme
3. Do undo

   **Expected:** exact pre-format text/script is returned
  
4. Do Redo
   
   **Expected:** formatting reapplies identically as on Step 2.

---

## P1-19

**Verify Undo/Redo functions properly on optimize-imports**

1. In a .py file add an **unused import** (e.g. "import random")
2. Run "Optimize Imports" (ctrl+opt+o / alt+ctrl+o / Code > Optimize Imports)
3. Do Undo

   **Expected:** the removed/optimized import returns in the same order as before.

4. Do Redo
   
   **Expected:** the unused import is removed/optimized again identically.

---

## P1-20

**Verify template expansion collapses by Undo and re-expands as is by Redo.**

1. In a .py file on a blank line type a template key - `main`
2. Expand it with the corresponding keymap (Tab / Enter)
   - Make sure the expansion took place and the following is now there as follows:
```python
   if __name__ == '__main__':


```    
3. Undo
   
   **Expected:** expansion collapses back to the original state

5. Redo
   
   **Expected:** The same template expands again, identically as on Step 2

---

## P1-21

**Verify that Undo/Redo properly removes and brings back generated boilerplate code (file)**

1. Right click on a folder
2. New > Python File
3. Click on "Python unit test", set name = `testBoilerplate`), press "Enter" (when prompted to Add File to Git, press "Cancel")

   **Expected:** new file is created and contains the generated boilerplate template

4. Undo

   **Expected:** the file is removed

5. Redo

   **Expected:** the file is recreated in the same folder with the same boilerplate.
   
---
