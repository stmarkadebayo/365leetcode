[Question](https://leetcode.com/problems/palindrome-number/)

### My Approach
---------------------
The approach uses a two-pointer technique to determine if a number is a palindrome. Here's the step-by-step breakdown:

1. **Handle negative numbers**: Negative numbers cannot be palindromes due to the negative sign, so we return False immediately.
2. **Convert to string**: Convert the number to a string to easily access individual digits.
3. **Two-pointer technique**: Use two pointers starting from the outside (left at start, right at end) and move towards the center.
4. **Compare digits**: At each step, compare the digits at the left and right pointers. If they don't match, return False.
5. **Terminate when pointers meet**: If the pointers meet or cross each other without finding mismatches, return True.

This approach efficiently checks for palindromes with O(n) time complexity where n is the number of digits, and O(n) space complexity for the string conversion.

### Implementation
-------------------------------
```python
class Solution(object):
    def isPalindrome(self, x):
        """
        :type x: int
        :rtype: bool
        """
        # step 1: Handle negatives immediately
        if x < 0:
            return False

        s = str(x)
        left = 0
        right = len(s) - 1

        # step 2: Shrink from the outside in (simpler than middle-out)
        while left < right:
            if s[left] != s[right]:
                return False # if they don't match, it's not a palindrome!
            left += 1
            right -= 1

        return True
```

### Complexities
---------------------------------
- **Time: O(n)** — We process each digit once in the worst case (when the number is a palindrome).
- **Space: O(n)** — String conversion requires space proportional to the number of digits.
