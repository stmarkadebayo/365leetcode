[Merge Two Sorted Lists](https://leetcode.com/problems/merge-two-sorted-lists/)

### My Approach
---------------------
Create a dummy first to track the new merged list. I used splicing here which means to change the pointers of the nodes instead of rewriting. So then, check and compare each list for the least number, add it to our dummy, check compare again and keep adding till all or one is done. 

Basically, we keep comparing the current nodes from both lists, take the smaller one, attach it to our merged list, and move forward in that list. When one list runs out, we just tack on whatever's left in the other list since it's already sorted.

### Implementation
-------------------------------
```python
class Solution:
    def mergeTwoLists(self, list1, list2):
        dummy = ListNode(0)
        current = dummy
        
        while list1 and list2:
            if list1.val < list2.val:
                current.next = list1 
                list1 = list1.next 
            else:
                current.next = list2  
                list2 = list2.next 
            current = current.next       

        current.next = list1 if list1 else list2
        
        return dummy.next
```

### Complexities
---------------------------------
- **Time: O(n + m)** — We traverse both lists once, comparing and merging elements
- **Space: O(1)** — Only using constant extra space with the dummy node, rearranging existing nodes
