[Remove Duplicates from Sorted Array](https://leetcode.com/problems/remove-duplicates-from-sorted-array/)

### My Approach
---------------------
Use two pointers to keep only unique values in place. The scanner pointer moves through the array to detect value changes, while the writer pointer marks the last confirmed unique position. When the scanner finds a new value, advance the writer and overwrite that position with the scanner value. This compacts all unique elements to the front in order, and the writer index plus one gives the count of unique elements.

### Implementation
-------------------------------
```python
class Solution:
    def removeDuplicates(self, nums):
        if not nums:
            return 0

        i = 0

        for j in range(1, len(nums)):
            if nums[j] != nums[i]:
                i += 1
                nums[i] = nums[j]

        return i + 1
```

### Complexities
---------------------------------
- **Time: O(n)** — Single pass through the array
- **Space: O(1)** — In-place updates only
