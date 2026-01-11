[Question](https://leetcode.com/problems/longest-common-prefix/)

### My Approach
---------------------
Use the first string as a template and iterate through each character. For each character position, check if it matches the same position in all other strings. Return the prefix up to the first mismatch position.

### Implementation
-------------------------------
```python
class Solution:
    def longestCommonPrefix(self, strs):
        if not strs:
            return ""

        # the first string is the template
        first = strs[0]

        # iterate through each character of the first string
        for i in range(len(first)):
            char = first[i]

            # 3. check this character against the same position in all other strings
            for j in range(1, len(strs)):
                if i == len(strs[j]) or strs[j][i] != char:
                    return first[:i]

        return first
```

### Complexities
---------------------------------
- **Time: O(m*n)** — where m is the length of the shortest string and n is the number of strings, as we may need to check all strings for each character position
- **Space: O(1)** — only using constant extra space excluding the input strings
