[Reverse Nodes in k-Group](https://leetcode.com/problems/reverse-nodes-in-k-group/)

### My Approach
---------------------
Walk a temporary pointer ahead `k` steps to confirm a full group exists. If you run out early, return `head` so the leftover nodes stay in their original order.  
Once a full group is confirmed, reverse exactly `k` nodes using the standard in-place reversal (prev/curr/next).  

After reversal, the original `head` becomes the tail of the group, so connect it to the result of reversing the remaining list.  
This keeps each `k`-sized block reversed while preserving any trailing nodes smaller than `k`.

### Implementation
-------------------------------
```python
class Solution:
    def reverseKGroup(self, head, k):
        temp = head
        for _ in range(k):
            if not temp:
                return head
            temp = temp.next

        prev = None
        curr = head
        for _ in range(k):
            nxt = curr.next
            curr.next = prev
            prev = curr
            curr = nxt

        head.next = self.reverseKGroup(curr, k)
        return prev
```

### Complexities
---------------------------------
- **Time: O(n)** - Each node is visited once
- **Space: O(n/k)** - Recursion depth for each group
