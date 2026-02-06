diff --git a//Users/mac/Desktop/365leetcode/problems/day36-combination-sum2.md b//Users/mac/Desktop/365leetcode/problems/day36-combination-sum2.md
@@ -0,0 +1,52 @@
+[Combination Sum II](https://leetcode.com/problems/combination-sum-ii/)
+
+### My Approach
+---------------------
+This is the same backtracking pattern as Combination Sum, with three key changes:
+
+- **Change 1:** Sort `candidates` first so duplicates are adjacent.
+- **Change 2:** Skip duplicate values at the same decision level using:
+  `if i > start and candidates[i] == candidates[i - 1]: continue`
+- **Change 3:** Recurse with `i + 1` so each element is used at most once.
+
+I track:
+
+- `remain`: amount left to reach `target`
+- `stack`: current combination
+- `start`: index to continue choices from
+
+If `remain == 0`, record the combination. If `remain < 0`, stop exploring that branch.
+
+### Implementation
+-------------------------------
+```python
+class Solution:
+    def combinationSum2(self, candidates: list[int], target):
+        results = []
+        candidates.sort()  # sort to handle duplicates
+
+        def backtrack(remain, stack, start):
+            if remain == 0:
+                results.append(list(stack))
+                return
+            if remain < 0:
+                return
+
+            for i in range(start, len(candidates)):
+                # if it's same as before it, skip
+                if i > start and candidates[i] == candidates[i - 1]:
+                    continue
+
+                stack.append(candidates[i])
+                # to prevent reuse of the same element
+                backtrack(remain - candidates[i], stack, i + 1)
+                stack.pop()
+
+        backtrack(target, [], 0)
+        return results
+```
+
+### Complexities
+---------------------------------
+- **Time: Exponential** - backtracking explores subsets; pruning and duplicate-skip reduce extra branches
+- **Space: O(n)** - recursion depth and current stack in the worst case
