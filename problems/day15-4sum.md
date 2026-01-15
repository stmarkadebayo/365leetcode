[4Sum](https://leetcode.com/problems/4sum/)

### My Approach
---------------------
It's just like the 3Sum I'd solved. First thing, sort the array to handle duplicates then use the two-pointer technique. Use nested loops for the first two elements (i and j), then use two pointers (left and right) to find the remaining two elements that sum to target - nums[i] - nums[j]. Skip duplicates at each level to avoid duplicate quadruplets.

### Implementation
-------------------------------
```python
class Solution:
    def fourSum(self, nums, target):
        nums.sort()
        res = []
        n = len(nums)

        for i in range(n):
            if i > 0 and nums[i] == nums[i-1]:
                continue
            for j in range(i + 1, n):
                if j > i + 1 and nums[j] == nums[j-1]:
                    continue

                l, r = j + 1, n - 1
                while l < r:
                    total = nums[i] + nums[j] + nums[l] + nums[r]
                    if total < target:
                        l += 1
                    elif total > target:
                        r -= 1
                    else:
                        res.append([nums[i], nums[j], nums[l], nums[r]])
                        l += 1
                        r -= 1
                        # skip duplicates for third and fourth numbers
                        while l < r and nums[l] == nums[l-1]:
                            l += 1
                        while l < r and nums[r] == nums[r+1]:
                            r -= 1
        return res
```

### Complexities
---------------------------------
- **Time: O(n³)** — Sorting takes O(n log n), then nested loops with two pointers give O(n³) in worst case, but often performs better due to early termination when sums exceed target
- **Space: O(1)** — Excluding output space, we only use a few variables and sort in-place
