[Substring with Concatenation of All Words](https://leetcode.com/problems/substring-with-concatenation-of-all-words/)

### My Approach
---------------------
I use a sliding window aligned to word boundaries. I pre-count the target frequency of each word. Then for each possible offset (0 to word_len - 1), I scan the string in word-sized steps, expanding the window to the right. 

If a word is valid, I add it to the current counts; if a word exceeds its target count, I shrink from the left until it is valid again. Whenever the number of words in the window matches the total word count, I record the left index. If I hit a word not in the target list, I reset the window and continue.

### Implementation
-------------------------------
```python
class Solution:
    def findSubstring(self, s, words):
        if not s or not words:
            return []

        word_len = len(words[0])
        word_count = len(words)

        target_counts = {}
        for w in words:
            target_counts[w] = target_counts.get(w, 0) + 1

        results = []

        for i in range(word_len):
            left = i
            right = i
            curr_counts = {}
            count = 0

            while right + word_len <= len(s):
                word = s[right : right + word_len]
                right += word_len

                if word in target_counts:
                    curr_counts[word] = curr_counts.get(word, 0) + 1
                    count += 1

                    while curr_counts[word] > target_counts[word]:
                        left_word = s[left : left + word_len]
                        curr_counts[left_word] -= 1
                        count -= 1
                        left += word_len

                    if count == word_count:
                        results.append(left)
                else:
                    # RESET: The "cat" scenario
                    curr_counts = {}
                    count = 0
                    left = right

        return results
```

### Complexities
---------------------------------
- **Time: O(n)** - Sliding window across each offset (word_len offsets overall)
- **Space: O(k)** - Hash maps for word counts, k = number of unique words
