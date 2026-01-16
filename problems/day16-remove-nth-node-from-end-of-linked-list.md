[Question: Remove Nth Node From End of List](https://leetcode.com/problems/remove-nth-node-from-end-of-list/)

### My Approach
---------------------
First, you can't know how the length of a linked list until you have travelled to the end. So here, we're going to use the fast-slow two pointer method. The fast pointer is ahead of the slow by n nodes, and they both keep moving one step at a time. By the time the fast gets to the end, the slow would be just right before the node that we need to remove. And in this case we do not actually remove it, we just point the node we're on to the node after the one we're removing.

### Implementation
-------------------------------
```python
class Solution:
    def removeNthFromEnd(self, head, n):       
        dummy = ListNode(0, head)  # this is for when the case where we need to remove the first node

        slow = fast = dummy
        for _ in range(n):
            fast = fast.next

        while fast.next:
            slow = slow.next
            fast = fast.next
            
        slow.next = slow.next.next
        return dummy.next         # return the actual head (which starts after our dummy)
```

### Complexities
---------------------------------
- **Time: O(n)** — We traverse the list twice: once to position the fast pointer n steps ahead, then once more to find the node to remove
- **Space: O(1)** — Only using a constant amount of extra space with the dummy node and two pointers
