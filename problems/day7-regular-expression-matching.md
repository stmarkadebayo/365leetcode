[Question](https://leetcode.com/problems/regular-expression-matching/)

### My Approach
---------------------
This solution required a two pointer dynamic programming approach. I used a strategy called Recursive Backtracking with Memoization. Here is the step-by-step logic:

1. **The Pointer Strategy**: Instead of modifying strings (which is slow), I use two "pointers" (i and j). i tracks our progress in the String, j tracks our progress in the Pattern. This allows us to look at specific characters without copying data.

2. **Identifying the "Fork in the Road"**: The hardest part of Regex is the *. It creates two simultaneous possibilities. Whenever I see a star, I force the computer to explore both:
   - The "Skip" Path: We treat a* as zero characters. We jump over that part of the pattern and keep the string exactly as it is.
   - The "Consume" Path: If the current character matches, we use the star to "eat" one letter from the string. Crucially, we don't move the pattern pointer forward yet, because the star might want to eat more letters in the next step.

3. **Handling the Wildcard**: The . is straightforward. In my matching logic, I treat . as a "Universal Match." If the pattern shows a ., the match variable is automatically True (as long as we haven't run out of string).

4. **Optimization (The "Sticky Note" Rule)**: In complex patterns like a*a*a*a*b, a standard recursive search will visit the same (i, j) coordinates thousands of times. I implement a Memoization Table (a dictionary). Before performing any calculation, the code checks if that (i, j) result is already in the table. This turns an "infinite" feeling problem into a simple grid of S × P calculations, ensuring the code passes even the toughest test cases.

### Implementation
-------------------------------
```python
class Solution:
    def isMatch(self, s, p):
        memo = {}

        def dp(i, j):
            # check if we've already solved this specific i and j
            if (i, j) in memo:
                return memo[(i, j)]

            # Base Case: If pattern is finished, string must be finished
            if j == len(p):
                return i == len(s)

            # check if characters at current positions match
            match = i < len(s) and (p[j] == s[i] or p[j] == '.')

            # handle the '*' Multiplier
            if j + 1 < len(p) and p[j+1] == '*':
                # option 1: ignore the 'char*' (move pattern pointer 2 steps)
                # option 2: use the 'char*' (if match, move string pointer 1 step)
                res = dp(i, j + 2) or (match and dp(i + 1, j))
            else:
                # no '*': move both pointers forward if they match
                res = match and dp(i + 1, j + 1)

            memo[(i, j)] = res
            return res

        return dp(0, 0)
```

### Complexities
---------------------------------
- **Time: O(S × P)** — Where S is the length of the string and P is the length of the pattern. We potentially visit each (i, j) combination once due to memoization.
- **Space: O(S × P)** — For the memoization table that stores results for each (i, j) combination, plus the recursion stack depth which is also O(S × P) in the worst case.