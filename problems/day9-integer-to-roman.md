[Question](https://leetcode.com/problems/integer-to-roman/)

### My Approach
---------------------
Create a list of all Roman numeral values in descending order, including the special subtractive cases (900=CM, 400=CD, 90=XC, 40=XL, 9=IX, 4=IV). By including these special cases, we automatically handle them without extra logic.

Then process the number greedily:
1. For each value in the list, find how many times it fits into num
2. Append that symbol that many times
3. Reduce num using modulo
4. Continue until num becomes 0

### Implementation
-------------------------------
```python
class Solution:
    def intToRoman(self, num):
        values = [
            (1000, "M"), (900, "CM"), (500, "D"), (400, "CD"),
            (100, "C"), (90, "XC"), (50, "L"), (40, "XL"),
            (10, "X"), (9, "IX"), (5, "V"), (4, "IV"), (1, "I")
        ]
        
        roman_parts = []
        
        for val, symbol in values:
            if num == 0:
                break
            
            count = num // val
            roman_parts.append(symbol * count)
            num %= val
            
        return "".join(roman_parts)
```

### Complexities
---------------------------------
- **Time: O(1)** — Fixed 13 values, always at most 13 iterations
- **Space: O(1)** — Fixed-size list, building output string only
