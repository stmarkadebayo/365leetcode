[Generate Parentheses](https://leetcode.com/problems/generate-parentheses/)

### My Approach
---------------------
Use backtracking to recursively build all valid parentheses combinations. Track counts of opening and closing brackets used. At each step, we have two choices: add an opening bracket '(' if we haven't used all n openings yet, or add a closing bracket ')' if we have more openings than closings (maintaining balance). When we reach a string of length 2n, it's a valid combination. This depth-first approach systematically explores the decision tree, backtracking when we hit dead ends or complete valid sequences, ensuring we generate all possible well-formed parentheses without duplicates.

### Implementation
-------------------------------
```python
class Solution:
    def generateParenthesis(self, n):
        res = []

        def backtrack(current_s, open_count, close_count):
            if len(current_s) == 2 * n:
                res.append(current_s)
                return

            if open_count < n:
                backtrack(current_s + "(", open_count + 1, close_count)

            if close_count < open_count:
                backtrack(current_s + ")", open_count, close_count + 1)

        backtrack("", 0, 0)
        return res
```

### Complexities
---------------------------------
- **Time: O(4^n / √n)** — The nth Catalan number represents the count of valid parentheses sequences, with the Catalan number formula C_n = (1/(n+1)) * (2n choose n) giving us the precise count, and the complexity reflects the exponential growth of valid combinations
- **Space: O(4^n / √n)** — For storing all valid parentheses combinations in the result list, with additional O(n) space used for the recursion stack depth
