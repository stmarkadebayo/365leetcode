[Rotate Image](https://leetcode.com/problems/rotate-image/)

### My Approach
---------------------
To rotate an `n x n` matrix 90 degrees clockwise in-place, I use two simple steps:

1. **Transpose the matrix** (swap across the main diagonal).
- This converts rows into columns.
- I only iterate the upper triangle (`j = i + 1` to `n - 1`) to avoid double swapping.

2. **Reverse each row**.
- After transposition, reversing each row gives the final clockwise rotation.

This is much cleaner than directly computing each element’s final position.

### Implementation
-------------------------------
```python
class Solution:
    def rotate(self, matrix: list[list[int]]) -> None:
        """
        Do not return anything, modify matrix in-place instead.
        """
        n = len(matrix)

        # transpose the matrix
        for i in range(n):
            for j in range(i + 1, n):
                matrix[i][j], matrix[j][i] = matrix[j][i], matrix[i][j]

        # then reverse each row
        for i in range(n):
            matrix[i].reverse()
```

### Complexities
---------------------------------
- **Time: O(n^2)**
- **Space: O(1)** (in-place)
