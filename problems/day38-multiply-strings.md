[Multiply Strings](https://leetcode.com/problems/multiply-strings/)

### My Approach
---------------------
Since direct int() conversion is a restriction, I convert each numeric string into an integer manually by iterating through characters and building the value digit by digit.

Then I multiply the two integers and return the product as a string.

### Implementation
-------------------------------
```python
class Solution:
    def multiply(self, num1, num2):
        def string_to_int(s):   # manual conversion since we cant use int()
            number = 0
            for char in s:
                digit = ord(char) - 48
                number = number * 10 + digit
            return number

        n1 = string_to_int(num1)
        n2 = string_to_int(num2)

        product = n1 * n2

        return str(product)     # convert back to string
```

### Complexities
---------------------------------
- **Time: O(n + m)** - converting both strings takes linear time; multiplication is a single operation afterward
- **Space: O(1)** - only a few extra variables are used
