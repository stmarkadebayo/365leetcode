[Question](https://leetcode.com/problems/3sum/)

### My Approach
---------------------
For this one, I had to sort the array first to be able to use the two-pointer technique and handle duplicates easily. Then iterate through each element as a potential first number in our triplet. For each position i:

1. If nums[i] > 0, break since all remaining numbers are also positive and can't sum to zero with two positive numbers
2. Skip duplicates by checking if nums[i] equals the previous element
3. Use two pointers (left = i+1, right = end) to find pairs that sum to -nums[i]:
   - If sum < 0, move left pointer right to increase sum
   - If sum > 0, move right pointer left to decrease sum
   - If sum == 0, add triplet and skip duplicates for both pointers

### Implementation
-------------------------------
```python
class Solution:
    def threeSum(self, nums):
        res = []
        nums.sort() #sorting the array

        for i in range(len(nums)):
            if nums[i] > 0:
                break

            if i > 0 and nums[i] == nums[i-1]:
                continue

            # two-pointer squeeze
            l, r = i + 1, len(nums) - 1
            while l < r:
                three_sum = nums[i] + nums[l] + nums[r]

                if three_sum < 0:
                    l += 1
                elif three_sum > 0:
                    r -= 1
                else:
                    res.append([nums[i], nums[l], nums[r]])
                    l += 1
                    r -= 1
                    # skip duplicate second and third numbers
                    while l < r and nums[l] == nums[l-1]:
                        l += 1
                    while l < r and nums[r] == nums[r+1]:
                        r -= 1

        return res
```

### Complexities
---------------------------------
- **Time: O(n²)** — sorting takes O(n log n), and the two-pointer approach takes O(n²) in the worst case
- **Space: O(1)** — excluding the output array, we use constant extra space (sorting is in-place)
