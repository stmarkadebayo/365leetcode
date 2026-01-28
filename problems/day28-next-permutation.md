[Next Permutation](https://leetcode.com/problems/next-permutation/)

### My Approach
---------------------
I scan from the right to find the first index where the sequence stops increasing (the pivot). If no such index exists, the array is in descending order and I reverse it to get the smallest permutation. 

Otherwise, I find the rightmost element larger than the pivot, swap them, and then reverse the suffix to make it the smallest possible arrangement after the pivot.

### Implementation
-------------------------------
```python
class Solution:
    def nextPermutation(self, nums):
        n = len(nums)

        # Find pivot: first index from right where nums[i] < nums[i+1]
        i = n - 2
        while i >= 0 and nums[i] >= nums[i + 1]:
            i -= 1

        if i >= 0:
            # Find rightmost successor to pivot
            j = n - 1
            while nums[j] <= nums[i]:
                j -= 1
            nums[i], nums[j] = nums[j], nums[i]

        # Reverse suffix
        left, right = i + 1, n - 1
        while left < right:
            nums[left], nums[right] = nums[right], nums[left]
            left += 1
            right -= 1
```

### Complexities
---------------------------------
- **Time: O(n)** - Single scan plus suffix reversal
- **Space: O(1)** - In-place operations only
