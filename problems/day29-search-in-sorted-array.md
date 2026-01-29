[Search in Rotated Sorted Array](https://leetcode.com/problems/search-in-rotated-sorted-array/)

### My Approach
---------------------
I use modified binary search. At each step, I check whether the left half is sorted or the right half is sorted.  
If the left half is sorted and the target lies within it, I move `right` leftward; otherwise I search the right half.  
If the right half is sorted and the target lies within it, I move `left` rightward; otherwise I search the left half.

### Implementation
-------------------------------
```python
class Solution:
    def search(self, nums, target):
        left, right = 0, len(nums) - 1
        
        while left <= right:
            mid = (left + right) // 2
            
            if nums[mid] == target:
                return mid
        
            # is left half sorted?
            if nums[left] <= nums[mid]:
                if nums[left] <= target < nums[mid]:
                    right = mid - 1
                else:
                    left = mid + 1
            
            # is right half sorted?
            else:
                if nums[mid] < target <= nums[right]:
                    left = mid + 1
                else:
                    right = mid - 1
                    
        return -1
```

### Complexities
---------------------------------
- **Time: O(log n)** - Binary search across rotated halves
- **Space: O(1)** - Constant extra space
