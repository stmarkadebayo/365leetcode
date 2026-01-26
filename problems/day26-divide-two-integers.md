[Divide Two Integers](https://leetcode.com/problems/divide-two-integers/)

### My Approach
---------------------
To divide without standard operators, I use a fast version of repeated subtraction that doubles the divisor to save time. I first determine the final sign and convert both numbers to positive to simplify the math. Instead of subtracting the divisor once at a time, I keep doubling it until it is the largest chunk that still fits inside the current dividend. After subtracting this large chunk, I add the corresponding count to the quotient. I repeat the process with the remaining dividend until it becomes smaller than the divisor. Finally, I apply the original sign and cap the result to stay within the 32-bit integer range.

### Implementation
-------------------------------
```python
class Solution:
    def divide(self, dividend, divisor):
        if dividend == -2147483648 and divisor == -1:
            return 2147483647

        negative = (dividend < 0) != (divisor < 0)

        a, b = abs(dividend), abs(divisor)
        res = 0

        while a >= b:
            temp_divisor = b
            count = 1

            while a >= (temp_divisor << 1):
                temp_divisor <<= 1
                count <<= 1

            a -= temp_divisor
            res += count

        return -res if negative else res
```

### Complexities
---------------------------------
- **Time: O((log |dividend|)^2)** - Doubling search per chunk and a logarithmic number of chunks
- **Space: O(1)** - Constant extra space
