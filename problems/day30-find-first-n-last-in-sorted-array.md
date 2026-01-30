[Find First and Last Position of Element in Sorted Array](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/)

### My Approach
---------------------
The **O(log n)** constraint hints at Binary Search. The only twist is to run it twice: one search to find the first (leftmost) occurrence, and another to find the last (rightmost).
When I hit the target, I still keep searching the half that could contain an earlier/later copy, while saving the current index as a candidate bound. This avoids any linear scan and still guarantees the earliest/latest position in a sorted array. If the first search fails, the target is not present at all.

### Implementation
-------------------------------
```python
class Solution:
    def searchRange(self, nums, target):
        def find_bound(is_left):
            left, right = 0, len(nums) - 1
            bound = -1
            
            while left <= right:
                mid = (left + right) // 2
                
                if nums[mid] == target:
                    bound = mid
                    if is_left:
                        right = mid - 1
                    else:
                        left = mid + 1
                elif nums[mid] < target:
                    left = mid + 1
                else:
                    right = mid - 1
            return bound

        start = find_bound(is_left=True)
        if start == -1:
            return [-1, -1]
        
        end = find_bound(is_left=False)
        return [start, end]
```

### Complexities
---------------------------------
- **Time: O(log n)** - Two binary searches
- **Space: O(1)** - Constant extra space
