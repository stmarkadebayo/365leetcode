[Question](https://leetcode.com/problems/longest-palindromic-substring/)

### My Approach
---------------------
The key insight is that palindromes are **symmetric around their center**. This means we can take every character (and every pair of adjacent characters) as a potential center, then expand outward to the left and right while the characters match.

For each position `i` in the string, I check two types of palindromes:
1. **Odd-length palindromes**: Center is at a single character `s[i]` (e.g., "aba" centered at 'b')
2. **Even-length palindromes**: Center is between `s[i]` and `s[i+1]` (e.g., "abba" centered between the two 'b's)

The `expandAroundCenter` helper function takes a left and right pointer, then expands outward while:
- Both pointers stay within bounds (`left >= 0` and `right < len(s)`)
- The characters at both positions match (`s[left] == s[right]`)

It returns the length of the palindrome found. The main function then calculates the start and end indices of this palindrome to extract the substring.

### Implementation
-------------------------------
```python
class Solution:
    def longestPalindrome(self, s):
        # handle edge case if input s is empty
        if not s:
            return ""
        
        # track start and end of best palindrome found
        start, end = 0, 0
        
        for i in range(len(s)):
            # check odd length palindromes (center is s[i])
            len1 = self.expandAroundCenter(s, i, i)
            # check even length palindromes (center is between s[i] and s[i+1])
            len2 = self.expandAroundCenter(s, i, i + 1)
            
            max_len = max(len1, len2)
            
            # update the start and end pointers if a longer palindrome is found
            if max_len > end - start:
                # subtract 1 because the center isn't always a single char
                start = i - (max_len - 1) // 2
                end = i + max_len // 2
                
        return s[start:end + 1]

    def expandAroundCenter(self, s, left, right):
        while left >= 0 and right < len(s) and s[left] == s[right]:
            left -= 1
            right += 1
        # returns the length of the palindrome found
        return right - left - 1
```

### Complexities
---------------------------------
- **Time: O(n²)** — We iterate through each of the n positions in the string. For each position, we expand outward which can take up to O(n) time in the worst case (when the entire string is a palindrome). So overall O(n × n) = O(n²)
- **Space: O(1)** — We only use a constant amount of extra space for variables (start, end, max_len, etc.)

