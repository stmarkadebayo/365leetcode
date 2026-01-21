[LeetCode Patterns Cheatsheet](../README.md)

### How To Pick A Pattern (Fast Triage)
---------------------
1) Need pairs or counts? -> Hash map
2) Sorted array or need to keep order? -> Two pointers
3) All combinations or permutations? -> Backtracking
4) Balanced or nested structure? -> Stack
5) Linked list with k-th from end? -> Two pointers (fast/slow)
6) "Closest" or fixed-size k-sum? -> Sort + two pointers
7) Patterned string conversion or parsing? -> Single pass scan
8) Two sorted arrays? -> Merge logic or binary search partition
9) Regex with .* or ? style? -> DP table

### Core Patterns (Based On This Repo)
---------------------
#### Hash Map (Counting / Lookup)
- Use when you need O(1) lookup for complements or counts.
- Typical steps: loop, check complement, store current.
- Example: `problems/day1-two-sum.md`

#### Two Pointers (Opposite Ends)
- Use on sorted arrays or when you can move inward based on comparison.
- Steps: `l=0`, `r=n-1`, move one pointer to improve target.
- Examples: `problems/day8-container-with-most-water.md`, `problems/day12-3sum.md`, `problems/day15-4sum.md`

#### Two Pointers (Slow/Fast)
- Use to remove duplicates or find k-th from end.
- Steps: slow marks write position, fast scans.
- Examples: `problems/day20-remove-dupes-from-sorted-array.md`, `problems/day16-remove-nth-node-from-end-of-linked-list.md`

#### Sliding Window
- Use when scanning a substring with constraints.
- Steps: expand right, shrink left to restore constraint, track best.
- Example: `problems/day2b-longest-substr-wo-repeating-char.md`

#### Stack
- Use for matching pairs or nested structure validation.
- Steps: push openings, pop on closing, validate types.
- Example: `problems/day17-valid-parentheses.md`

#### Backtracking (Decision Tree)
- Use for generating all valid combinations.
- Steps: choose, recurse, un-choose; prune invalid paths early.
- Examples: `problems/day14-letter-combos-of-a-phone-num.md`, `problems/day19-generate-parentheses.md`

#### Sorting + Two Pointers (k-Sum Family)
- Use for 3Sum/4Sum/Closest. Sort first, fix one or two elements, scan.
- Steps: sort, loop fixed index, then two pointers for remainder.
- Examples: `problems/day12-3sum.md`, `problems/day13-3sum-closest.md`, `problems/day15-4sum.md`

#### Merge Logic (Two Sorted Lists/Arrays)
- Use when combining two sorted inputs.
- Steps: compare heads, append smaller, advance.
- Example: `problems/day18-merge-two-sorted-lists.md`

#### Divide And Conquer / Binary Search Partition
- Use for median of two sorted arrays.
- Steps: partition so left max <= right min, adjust by binary search.
- Example: `problems/day3-median-of-two-sorted-arrays.md`

#### String Scan / Parsing
- Use for atoi, roman conversion, or any format parsing.
- Steps: skip prefix, handle sign, parse digits/symbols, clamp if needed.
- Examples: `problems/day6-string-to-integer(atoi).md`, `problems/day9-integer-to-roman.md`, `problems/day10-roman-to-integer.md`

#### DP (Regex Style)
- Use when matching with wildcard operators (`.` or `*`) over full strings.
- Steps: dp[i][j] = match of s[:i] and p[:j].
- Example: `problems/day7-regular-expression-matching.md`

### Quick Complexity Hints
---------------------------------
- Two pointers / sliding window: O(n) time, O(1) space
- Hash map: O(n) time, O(n) space
- Backtracking: exponential in n (output size dominates)
- Sorting + two pointers: O(n log n) + O(n^2) typical for k-sum
- Stack: O(n) time, O(n) space

### Writing A Solution (Template)
---------------------------------
1) State the invariant (what your pointers/stack represent)
2) Describe how you move/update it
3) Explain when you record an answer
4) Give time/space complexity
