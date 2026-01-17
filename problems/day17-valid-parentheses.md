[Valid Parentheses](https://leetcode.com/problems/valid-parentheses/)

### My Approach
---------------------
Use a stack to track opening brackets. When encountering a closing bracket, check if it matches the top of the stack. If it matches, pop the stack; if not or stack is empty, return false. At the end, stack should be empty for valid parentheses.

### Implementation
-------------------------------
```python
class Solution:
    def isValid(self, s):
        mapping = {")": "(", "}": "{", "]": "["}
        stack = []

        for char in s:
            if char in mapping:
                top_element = stack.pop() if stack else '#'

                if mapping[char] != top_element:
                    return False
            else:
                stack.append(char)

        # if the stack is empty, all brackets were matched correctly
        return not stack
```

### Complexities
---------------------------------
- **Time: O(n)** — Single pass through the string
- **Space: O(n)** — Stack stores up to n/2 opening brackets in worst case
