[Question](https://leetcode.com/problems/string-to-integer-atoi/)

### My Approach
---------------------
The question already gives us what the atoi algorithm is. All that's left is to implement. Here's the step-by-step breakdown of how I did it:

1. **Skip leading whitespace**: Iterated through the string until I found the first non-whitespace character.
2. **Determine sign**: Checked if the next character is '+' or '-' to set the sign multiplier (default is positive).
3. **Read digits**: Processed consecutive digits, building the number while skipping leading zeros.
4. **Apply sign**: Multiplied the accumulated result by the sign.
5. **Clamp to 32-bit range**: Ensured the result stays within [-2³¹, 2³¹-1] by rounding to the nearest boundary if needed.

This approach efficiently handles all the specified requirements while maintaining O(n) time complexity where n is the string length.

### Implementation
-------------------------------
```python
class Solution(object):
    def myAtoi(self, s):
        """
        :type s: str
        :rtype: int
        """
        n = len(s)
        i = 0
        result = 0
        sign = 1

        # 1: skip leading whitespace
        while i < n and s[i] == ' ':
            i += 1

        # 2: check for sign
        if i < n and s[i] == '+':
            sign = 1
            i += 1
        elif i < n and s[i] == '-':
            sign = -1
            i += 1

        # 3: read digits and build the number
        while i < n and s[i].isdigit():
            digit = int(s[i])
            result = (result * 10) + digit
            i += 1

        # apply the sign to our result
        result = result * sign

        # 4: clamping (32-bit signed integer limits)
        MAX_INT = 2147483647
        MIN_INT = -2147483648

        if result > MAX_INT:
            return MAX_INT
        if result < MIN_INT:
            return MIN_INT

        return result
```

### Complexities
---------------------------------
- **Time: O(n)** — Single pass through the string with constant-time operations for each character.
- **Space: O(1)** — Only a few variables are used regardless of input size.
