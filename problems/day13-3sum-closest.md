[Question](https://leetcode.com/problems/3sum-closest/)

### My Approach
---------------------
This problem is similar to the 3Sum problem, but instead of finding triplets that sum to zero, I needed to find the triplet whose sum is closest to the target value. After sorting the array, I fixed one element and use two pointers to find the optimal pair for the remaining elements.

For each position i, I:
1. Used two pointers (left = i+1, right = end) to scan through the remaining elements
2. Calculated the current sum of nums[i] + nums[left] + nums[right]
3. If the current sum equals the target, return it immediately (perfect match)
4. Otherwise, check if the absolute difference |target - current_sum| is smaller than our current closest difference

### Implementation
-------------------------------
```python
class Solution:
    def threeSumClosest(self, nums: list[int], target: int) -> int:
        nums.sort()
        closest_sum = nums[0] + nums[1] + nums[2]

        for i in range(len(nums) - 2):
            l, r = i + 1, len(nums) - 1

            while l < r:
                current_sum = nums[i] + nums[l] + nums[r]
                if current_sum == target:
                    return current_sum

                if abs(target - current_sum) < abs(target - closest_sum):
                    closest_sum = current_sum

                # move pointers based on whether we are too high or too low
                if current_sum < target:
                    l += 1
                else:
                    r -= 1

        return closest_sum
```

### Complexities
---------------------------------
- **Time: O(n²)** — sorting takes O(n log n), and the nested loops with two pointers take O(n²) in the worst case
- **Space: O(1)** — we use constant extra space, with sorting done in-place
