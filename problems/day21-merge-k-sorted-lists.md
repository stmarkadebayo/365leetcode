[Merge k Sorted Lists](https://leetcode.com/problems/merge-k-sorted-lists/)

### My Approach
---------------------
Use a min-heap to always pull the smallest current node among the k lists. First, push the head of each list into the heap (store value, list index, and node). Then repeatedly pop the smallest node, attach it to the merged list, and push that node's next into the heap. A dummy node makes it easy to build the result by splicing existing nodes.

### Implementation
-------------------------------
```python
import heapq

class Solution:
    def mergeKLists(self, lists):
        # 1. Setup the Heap and the Dummy Node
        min_heap = []
        dummy = ListNode(0)
        curr = dummy
        
        # 2. Put the head of every list into the heap
        # We store (value, list_index, node) so the heap can sort by value
        for i, l in enumerate(lists):
            if l:
                heapq.heappush(min_heap, (l.val, i, l))
        
        # 3. While there are nodes in the heap...
        while min_heap:
            val, i, node = heapq.heappop(min_heap)
            
            # Add the smallest node to our merged list
            curr.next = node
            curr = curr.next
            
            # If that list has another node, add it to the heap
            if node.next:
                heapq.heappush(min_heap, (node.next.val, i, node.next))
        
        return dummy.next
```

### Complexities
---------------------------------
- **Time: O(N log k)** - Each of N nodes is pushed/popped from the heap of size k
- **Space: O(k)** - Heap holds at most one node per list
