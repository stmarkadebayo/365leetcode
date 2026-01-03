[Question](https://leetcode.com/problems/median-of-two-sorted-arrays/)

### My Approach
---------------------
This one was quite tough. My first instinct was to merge both arrays and find the median from the merged array. This would be a valid and correct solution - we merge the two sorted arrays, then find the middle element(s). However, the problem constraint requires our solution to be O(log(m+n)), and merging takes O(m+n) time.

To achieve O(log(m+n)), I use **binary search** with a partitioning approach. The key insight: you don't need to actually merge the arrays! Instead, we can partition both arrays such that the left partition contains exactly half the elements (rounded up), and all elements in the left partition are ≤ all elements in the right partition. The median is at the boundary between these partitions.

Then binary search on the smaller array to find the partition point `i`. For each candidate partition in `nums1`, I calculate the corresponding partition point `j` in `nums2` such that `i + j = (m+n+1)//2` (ensuring the left partition has the correct size). Then I check if the partition is valid:
- `nums1[i-1] <= nums2[j]` (last element of nums1's left ≤ first element of nums2's right)
- `nums2[j-1] <= nums1[i]` (last element of nums2's left ≤ first element of nums1's right)

If both conditions hold, I found the correct partition. The median is `max(left elements)` for odd length, or `(max(left) + min(right)) / 2` for even length. If the partition is invalid, I adjust the binary search range - if `nums1[i-1] > nums2[j]`, I move the partition left (too many from nums1), otherwise move right.

I handle edge cases by using `-inf` when `i==0` or `j==0`, and `inf` when `i==m` or `j==n` to cover cases where one array contributes all elements to one side.

### Implementation
-------------------------------
```python
class Solution:
    def findMedianSortedArrays(self, nums1, nums2):
        # Ensure nums1 is the smaller array
        if len(nums1) > len(nums2):
            nums1, nums2 = nums2, nums1
        
        m, n = len(nums1), len(nums2)
        left, right = 0, m
        total_left = (m + n + 1) // 2
        
        while left <= right:
            # Partition nums1 at position i
            i = (left + right) // 2
            # Partition nums2 at position j
            j = total_left - i
            
            # Handle edge cases for boundaries
            nums1_left = float('-inf') if i == 0 else nums1[i - 1]
            nums1_right = float('inf') if i == m else nums1[i]
            nums2_left = float('-inf') if j == 0 else nums2[j - 1]
            nums2_right = float('inf') if j == n else nums2[j]
            
            # Check if partition is valid
            if nums1_left <= nums2_right and nums2_left <= nums1_right:
                # Found correct partition
                if (m + n) % 2 == 1:
                    # Odd length: median is max of left partition
                    return max(nums1_left, nums2_left)
                else:
                    # Even length: median is average of max(left) and min(right)
                    return (max(nums1_left, nums2_left) + min(nums1_right, nums2_right)) / 2.0
            elif nums1_left > nums2_right:
                # Too many elements from nums1 in left partition, move left
                right = i - 1
            else:
                # Too few elements from nums1 in left partition, move right
                left = i + 1
```

### Complexities
---------------------------------
- **Time: O(log(min(m, n)))** — Binary search on the smaller array, each iteration is O(1)
- **Space: O(1)** — Only using a constant amount of extra space
