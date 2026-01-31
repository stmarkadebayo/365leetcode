[Search Insert Position](https://leetcode.com/problems/search-insert-position/)

### My Approach
---------------------
This is the simplest form of binary search. You just keep shrinking the search window based on how `nums[mid]` compares to the target. If you find the target, return its index. If you never find it, the `left` pointer ends up at the exact spot where the target should be inserted in order to keep the array sorted. That makes the solution both clean and optimal.

### Implementation
-------------------------------
```python
class Solution:
    def searchInsert(self, nums: list[int], target: int) -> int:
        left = 0
        right = len(nums) - 1
        
        while left <= right:
            mid = (left + right) // 2
            
            if nums[mid] == target:
                return mid
            elif nums[mid] < target:
                left = mid + 1
            else:
                right = mid - 1
                
        # If we didn't find it, 'left' is the insertion index.
        return left
```

### Complexities
---------------------------------
- **Time: O(log n)** - Standard binary search
- **Space: O(1)** - Constant extra space
