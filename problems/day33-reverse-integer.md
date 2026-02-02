[Reverse Integer](https://leetcode.com/problems/reverse-integer/)

### My Approach
---------------------
The most straightforward way to reverse an integer is to temporarily convert it into a string. By treating the number as text, I can use Python’s slicing to flip the order of the characters. I handle negative numbers by keeping the minus sign in place while only reversing the digits that follow it. 

Once the characters are in reverse order, I convert the string back into an integer. Because the problem has strict 32-bit limits, my final step is to verify that this new number isn't too large or too small for the allowed range. If it falls outside those boundaries, I simply return zero.

### Implementation
-------------------------------
```python
class Solution:
    def reverse(self, x):
        # handle the negative sign separately and add it back after reversal
        s = str(x)
        if s[0] == '-':
            reversed_s = '-' + s[1:][::-1]
        else:
            reversed_s = s[::-1]

        res = int(reversed_s)

        if res < -2**31 or res > 2**31 - 1:
            return 0

        return res
```

### Complexities
---------------------------------
- **Time: O(n)** - n is the number of digits
- **Space: O(n)** - string copy for the reversal
