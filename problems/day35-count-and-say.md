[Count and Say](https://leetcode.com/problems/count-and-say/)

### My Approach
---------------------
I treat the problem as a simple string-building exercise that repeats for a set number of rounds. In each round, I iterate through the current sequence and keep track of how many times the same digit appears in a row. As long as the current digit matches the one next to it, I increment a counter. 

The moment I encounter a different digit or reach the very end of the string, I record my findings by appending the count and the digit to a new result. After documenting every group in the sequence, I reset the counter and move on to the next round. 

This continues until I have transformed the string exactly n−1 times. By using basic string addition and a single loop, I keep the logic transparent and easy to follow.

### Implementation
-------------------------------
```python
class Solution:
    def countAndSay(self, n):
        current_string = "1"

        for _ in range(n - 1):
            next_string = ""
            count = 1

            for i in range(len(current_string)):
                if i + 1 < len(current_string) and current_string[i] == current_string[i + 1]:
                    count += 1
                else:
                    next_string = next_string + str(count) + current_string[i]
                    count = 1

            current_string = next_string

        return current_string
```

### Complexities
---------------------------------
- **Time: O(L * n)** - L is the length of the current string in each round
- **Space: O(L)** - for the next string built each round
