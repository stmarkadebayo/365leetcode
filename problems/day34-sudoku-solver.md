[Sudoku Solver](https://leetcode.com/problems/sudoku-solver/)

### My Approach
---------------------
This solution uses classic backtracking with bookkeeping to prune choices quickly. I scan the board once to populate three sets per row, column, and 3x3 box, and I record all empty cells in a list. 

During backtracking, I fill cells in the order they appear in that list. For each empty cell, I try digits 1–9 and only place a digit if it does not already exist in the corresponding row, column, or box. If a placement leads to a dead end, I undo it and continue trying other digits. When all empty cells are filled, the board is solved in place.

### Implementation
-------------------------------
```python
class Solution:
    def solveSudoku(self, board: list[list[str]]):
        rows = [set() for _ in range(9)]
        cols = [set() for _ in range(9)]
        boxes = [set() for _ in range(9)]
        empty_cells = []

        for r in range(9):
            for c in range(9):
                val = board[r][c]
                if val != ".":
                    rows[r].add(val)
                    cols[c].add(val)
                    boxes[(r // 3) * 3 + (c // 3)].add(val)
                else:
                    empty_cells.append((r, c))

        def backtrack(index):
            if index == len(empty_cells):
                return True

            r, c = empty_cells[index]
            box_idx = (r // 3) * 3 + (c // 3)

            for num in "123456789":
                # instant check using our sets
                if num not in rows[r] and num not in cols[c] and num not in boxes[box_idx]:
                    # place the number and update memory
                    board[r][c] = num
                    rows[r].add(num)
                    cols[c].add(num)
                    boxes[box_idx].add(num)

                    if backtrack(index + 1):  # move to the next empty cell
                        return True

                    board[r][c] = "."
                    rows[r].remove(num)
                    cols[c].remove(num)
                    boxes[box_idx].remove(num)

            return False

        backtrack(0)
```

### Complexities
---------------------------------
- **Time: O(9^E)** - E is the number of empty cells; pruning reduces the search in practice
- **Space: O(1)** - constant extra space for sets and recursion depth bounded by 81
