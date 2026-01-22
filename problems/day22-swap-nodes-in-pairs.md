[Swap Nodes in Pairs](https://leetcode.com/problems/swap-nodes-in-pairs/)

### My Approach
---------------------
Use a dummy node so swaps near the head are handled the same as the rest. Maintain a `prev` pointer to the node before the current pair. 

For each pair, store `first` and `second`, then rewire `first.next`, `second.next`, and `prev.next` to flip them. Move `prev` to `first` (the new tail of the pair) and repeat. This keeps the swaps in-place and the pointer updates consistent.

### Implementation
-------------------------------
```python
class Solution:
    def swapPairs(self, head):
        dummy = ListNode(0, head)
        prev = dummy
        
        while prev.next and prev.next.next: # ensures there are at least two nodes left to swap
            first = prev.next
            second = prev.next.next

            first.next = second.next  # 1 points to 3
            second.next = first       # 2 points to 1
            prev.next = second        # prev points to 2
            
            # then move prev forward to the start of the next pair
            prev = first
            
        return dummy.next
```

### Complexities
---------------------------------
- **Time: O(n)** - Each node is visited once
- **Space: O(1)** - In-place pointer swaps
