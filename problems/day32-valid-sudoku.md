[Valid Sudoku](https://leetcode.com/problems/valid-sudoku/)

### My Approach
---------------------
This is basically a one-pass check that uses 27 sets: 9 for rows, 9 for columns, and 9 for the 3x3 boxes. As I move through the board, I skip dots and figure out which row, column, and box the current number belongs to. 

If that number is already in any of those sets, it means we’ve seen a duplicate in the same row, column, or box, so I can return False immediately. If not, I add it to all three sets and keep going. If I finish the entire board without a conflict, then every number was unique in its row, column, and box, so the board is valid.

### Implementation
-------------------------------
```python
class Solution:
    def isValidSudoku(self, board):
        rows = [set() for _ in range(9)]
        cols = [set() for _ in range(9)]
        boxes = [set() for _ in range(9)]

        for r in range(9):
            for c in range(9):
                val = board[r][c]
                if val == ".":
                    continue

                box_idx = (r // 3) * 3 + (c // 3)

                if val in rows[r] or val in cols[c] or val in boxes[box_idx]:
                    return False

                rows[r].add(val)
                cols[c].add(val)
                boxes[box_idx].add(val)

        return True
```

### Complexities
---------------------------------
- **Time: O(1)** - Fixed 9x9 board, constant work
- **Space: O(1)** - Fixed-size sets (bounded by 9x9)
