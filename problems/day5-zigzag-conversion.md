[Question](https://leetcode.com/problems/zigzag-conversion/)

### My Approach
---------------------
I had to think of the movement as an elevator. It goes: Floor 0 → 1 → 2 → 3 (Bottom) → 2 → 1 → 0 (Top) → 1...

The Rule: You move down until you hit the last floor, then you reverse and move up until you hit the first floor. So then it is important to track the current row(floor) and the movement at each level.

My solution strategy:
1. **Base Case Handling**: If numRows is 1 or greater than/equal to string length, return the string as-is (no zigzag possible)
2. **Row Tracking**: Create a list of strings to represent each row
3. **Direction Management**: Use a step variable (1 for down, -1 for up) to control movement
4. **Character Placement**: Iterate through each character, placing it in the current row
5. **Direction Reversal**: Change direction when hitting top (row 0) or bottom (row numRows-1)

### Implementation
-------------------------------
```python
class Solution:
    def convert(self, s, numRows):
        # if only one row, no zigzag is possible
        if numRows == 1 or numRows >= len(s):
            return s

        # create the "buckets" for each row
        rows = [""] * numRows
        current_row = 0
        step = 1  # 1 means moving down, -1 means moving up

        # iterate through the characters and simulate the movement
        for char in s:
            rows[current_row] += char

            # if we hit the top or bottom, reverse the direction
            if current_row == 0:
                step = 1
            elif current_row == numRows - 1:
                step = -1

            # move the elevator to the next floor
            current_row += step

        # combine all rows into a single string
        return "".join(rows)
```

### Complexities
---------------------------------
- **Time: O(n)** — Single pass through the string with constant-time operations for each character, plus O(n) for joining rows.
- **Space: O(n)** — Storage for rows list and output string, both proportional to input size.
