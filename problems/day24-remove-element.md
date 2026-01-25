[Remove Element](https://leetcode.com/problems/remove-element/)

### My Approach
---------------------
This is a two-pointer technique where i scans every number and k rewrites the ones we want to keep. Instead of deleting (which would shift everything), we compact the array toward the front by overwriting "bad" values with the next "good" value. The writer pointer k acts like a boundary for the clean portion. Each time the reader finds a number we keep, it writes it at k and moves k forward. By the end, all unwanted values are ignored or overwritten, and k is the count of valid elements.

### Implementation
-------------------------------
```python
class Solution:
    def removeElement(self, nums, val):
        k = 0

        for i in range(len(nums)):
            if nums[i] != val:
                nums[k] = nums[i]
                k += 1

        return k
```

### Complexities
---------------------------------
- **Time: O(n)** - Single pass through the array
- **Space: O(1)** - In-place updates only
