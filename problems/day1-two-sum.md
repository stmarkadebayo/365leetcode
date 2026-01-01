[Question](https://leetcode.com/problems/two-sum/)

### My Approach
---------------------
The common way is to brute-force, that'll be straightforward and correct. It involves checking every possible pair of elements using two nested loops: for each index `i`, iterate over all indices `j > i`, compute the sum `nums[i] + nums[j]`, and return `[i, j]` if it equals the target. This exhaustively examines all unique pairs and guarantees finding the solution given the problem constraints.

However, this achieves O(n²) time complexity, making it inefficient for larger inputs where n approaches 10⁴.

For better performance by reducing the time complexity, I leverage the fact that for any element `nums[i]`, the required second number is exactly `target - nums[i]` (the complement). Use a hash map to store previously seen numbers and their indices. During a single pass through the array:

- Compute the complement of the current element.
- Check if this complement exists in the hash map.
- If found, return the stored index and the current index.
- Otherwise, add the current number and its index to the hash map.

This ensures each element is processed only once, yielding O(n) time complexity with O(n) additional space.


### Implementation
-------------------------------
```python
class Solution:
    def twoSum(self, nums, target):
        seen = {}
        for i in range(len(nums)):
            complement = target - nums[i]
            if complement in seen:
                return [seen[complement], i]
            seen[nums[i]] = i
```

### Complexities
---------------------------------
- **Time: O(n)** — Single pass through the array with constant-time hash operations.
- **Space: O(n)** — Hash map stores up to n elements in the worst case.
