[Find the Index of the First Occurrence in a String](https://leetcode.com/problems/find-the-index-of-the-first-occurrence-in-a-string/)

### My Approach
---------------------
This is the straightforward sliding window check. I line up needle at every possible start in haystack and compare characters one by one. If any character mismatches, I break early and move the window forward. The first full match returns that start index, and if none match, return -1.

### Implementation
-------------------------------
```python
class Solution:
    def strStr(self, haystack, needle):
        n = len(needle)
        h = len(haystack)

        for i in range(h - n + 1):
            match = True
            for j in range(n):
                if haystack[i + j] != needle[j]:
                    match = False
                    break

            if match:
                return i

        return -1
```

### Complexities
---------------------------------
- **Time: O(h * n)** - Worst case checks each window of size n
- **Space: O(1)** - Constant extra space
