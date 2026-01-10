[Question](https://leetcode.com/problems/roman-to-integer/)

### My Approach
---------------------
Instead of trying to find pairs like "IV" or "CM" first, we can just walk through the string one character at a time and apply this one simple rule:

Look at the current value and the next value.

If the current value is smaller than the one after it, it means we are in a subtractive case. We subtract the current value from our total.

Otherwise, we add the current value to our total.

### Implementation
-------------------------------
```python
class Solution:
    def romanToInt(self, s):
        roman_map = {
            'I': 1, 'V': 5, 'X': 10, 'L': 50,
            'C': 100, 'D': 500, 'M': 1000
        }
        
        total = 0
        n = len(s)
  
        for i in range(n):
            current_val = roman_map[s[i]]
            
            if i + 1 < n and current_val < roman_map[s[i+1]]:
                total -= current_val
            else:
                total += current_val
                
        return total
```

### Complexities
---------------------------------
- **Time: O(n)** — Single pass through the string of length n
- **Space: O(1)** — Fixed-size hashmap and constant extra space
