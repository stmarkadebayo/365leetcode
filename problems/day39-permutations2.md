[Permutations II](https://leetcode.com/problems/permutations-ii/)

### My Approach
---------------------
I use backtracking with a frequency map (`Counter`) so duplicate values are handled naturally.

At each step, I try every number that still has remaining count:
- choose it (append to path, decrement count)
- recurse
- undo the choice (increment count, pop from path)

When the path length equals `len(nums)`, I add it to `results`.

### Implementation
-------------------------------
```python
from collections import Counter

class Solution:
    def permuteUnique(self, nums: list[int]):
        results = []
        counts = Counter(nums)
        
        def backtrack(path):
            if len(path) == len(nums):
                results.append(list(path))
                return
            
            for num in counts:
                if counts[num] > 0:
                    path.append(num)
                    counts[num] -= 1
                    
                    backtrack(path)
                    
                    counts[num] += 1
                    path.pop()
        
        backtrack([])
        return results
```

### Complexities
---------------------------------
- **Time: O(n * n!)** in the worst case (all numbers distinct), with less branching when duplicates exist
- **Space: O(n)** for recursion/path (excluding output)
