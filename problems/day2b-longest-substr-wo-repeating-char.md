[Question](https://leetcode.com/problems/longest-substring-without-repeating-characters/)

### My Approach
---------------------
This is a classic **sliding window** problem. So I used two pointers (`left` and `right`) to define the current substring window, and a hash map to track the last index where each character was seen.

The key insight: when we encounter a duplicate character, we need to move the `left` pointer to just after the previous occurrence of that character. This ensures our window always contains unique characters.

Algorithm:
- Use `right` pointer to expand the window by including new characters
- Use hash map `seen` to store character → last index mapping
- When duplicate found (character exists in map AND its index is within current window), move `left` to `seen[character] + 1`
- Track maximum window size as we expand

The hash map allows O(1) lookup to check if we've seen a character before, making the overall solution O(n) time.

### Implementation
-------------------------------
```python
class Solution:
    def lengthOfLongestSubstring(self, s):
        seen = {}
        left = 0
        max_len = 0
        
        for right in range(len(s)):
            if s[right] in seen and seen[s[right]] >= left:
                left = seen[s[right]] + 1
            seen[s[right]] = right
            max_len = max(max_len, right - left + 1)
        
        return max_len
```

### Complexities
---------------------------------
- **Time: O(n)** — Single pass through the string, each character visited once
- **Space: O(min(n, m))** — Hash map stores at most min(n, m) characters where m is character set size (128 for ASCII)