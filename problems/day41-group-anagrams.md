[Group Anagrams](https://leetcode.com/problems/group-anagrams/)

### My Approach
---------------------
I group words by a canonical key: the sorted version of each string.

For every string in `strs`:
- sort its characters (for example, `"eat"` and `"tea"` both become `"aet"`)
- use that sorted string as a hash map key
- append the original string to that key's list

At the end, each list in the map is one anagram group, so I return all grouped values.

### Implementation
-------------------------------
```python
from collections import defaultdict

class Solution:
    def groupAnagrams(self, strs: list[str]):
        buckets = defaultdict(list)
        
        for s in strs:
            sorted_key = "".join(sorted(s))
            buckets[sorted_key].append(s)
            
        return list(buckets.values())
```

### Complexities
---------------------------------
- **Time: O(n * k log k)** where `n` is the number of strings and `k` is the average string length
- **Space: O(n * k)** for storing grouped strings and keys
