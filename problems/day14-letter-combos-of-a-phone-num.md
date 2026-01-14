[Question](https://leetcode.com/problems/letter-combinations-of-a-phone-number/)

### My Approach
---------------------
My solution here implements Depth First Search (DFS) through backtracking to generate all possible letter combinations. The approach is to systematically explore every possible combination by trying each letter for a digit before moving to the next digit, essentially building the combinations one character at a time until we've used all digits.

We start with a phone keypad mapping dictionary, then use a recursive backtrack function that:
1. Takes the current position in the digits string and the current combination path
2. If the path length matches the digits length, we've found a complete combination
3. Otherwise, get all possible letters for the current digit and try each one recursively
4. After trying each possibility, backtrack by removing the last added letter to try the next option

It's like exploring a tree where each level represents a digit, and each branch represents choosing a specific letter for that digit. We traverse depth-first, collecting all complete paths.

### Implementation
-------------------------------
```python
class Solution:
    def letterCombinations(self, digits):
        if not digits:
            return []
        
        phone = {
            "2": "abc", "3": "def", "4": "ghi", "5": "jkl",
            "6": "mno", "7": "pqrs", "8": "tuv", "9": "wxyz"
        }
        
        res = []
        
        def backtrack(index, path):
            if len(path) == len(digits):
                res.append("".join(path))
                return
            
            possible_letters = phone[digits[index]]

            for letter in possible_letters:
                path.append(letter)
                backtrack(index + 1, path)
                
                path.pop()

        # restart the process from index 0 with an empty path
        backtrack(0, [])
        return res
```

### Complexities
---------------------------------
- **Time: O(3^n × 4^m)** — where n is count of digits with 3 letters (2,3,4,5,6,8) and m is count of digits with 4 letters (7,9). Each digit branches into 3 or 4 possibilities
- **Space: O(3^n × 4^m)** — for storing all combinations in the result list, plus O(n) for the recursion stack
