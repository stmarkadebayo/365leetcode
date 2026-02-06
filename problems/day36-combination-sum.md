[Combination Sum](https://leetcode.com/problems/combination-sum/)

### My Approach
---------------------
I use backtracking to build combinations that sum to `target`. At each step I track:

- `remain`: how much is left to reach the target
- `stack`: the current combination being built
- `start`: the index in `candidates` to continue from (so we don’t generate duplicate permutations)

If `remain == 0`, the current `stack` is a valid combination and gets recorded. If `remain < 0`, that path is impossible and we stop exploring it. Otherwise, we try each candidate from `start` onward, allowing reuse of the same number by recursing with the same index `i`.

### Implementation
-------------------------------
```python
class Solution:
    def combinationSum(self, candidates: list[int], target):
        results = []

        def backtrack(remain, stack, start):
            if remain == 0:
                results.append(list(stack))
                return

            if remain < 0:
                return

            for i in range(start, len(candidates)):
                num = candidates[i]

                stack.append(num)
                backtrack(remain - num, stack, i)
                stack.pop()

        backtrack(target, [], 0)
        return results
```

### Complexities
---------------------------------
- **Time: Exponential** - depends on the number of valid combinations explored
- **Space: O(T / m)** - recursion depth and current stack, where `T` is `target` and `m` is `min(candidates)`
