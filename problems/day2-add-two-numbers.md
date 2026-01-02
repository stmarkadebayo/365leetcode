[Question](https://leetcode.com/problems/add-two-numbers/)

### My Approach
---------------------
We have two numbers stored as linked lists in **reverse order** (least significant digit first). Since digits are reversed, we process from head to tail (left to right), which is the same as adding from right to left on paper!

The key insight is to simulate the normal manual addition:
- Start from the beginning of both lists (since they're reversed)
- Add corresponding digits plus any carry from the previous step
- If sum >= 10, the new digit is (sum % 10) and carry is (sum // 10)
- Since max sum is 9 + 9 + 1 = 19, carry is always 0 or 1
- Continue until both lists are processed AND carry is 0

I use a **dummy head pattern** to simplify linked list construction - this avoids special cases for the first node and makes the code cleaner. The dummy head is just a placeholder; we return `dummy.next` to skip it.

For different length lists, I treat exhausted lists as 0. This handles edge cases naturally without extra complexity.

### Implementation
-------------------------------
```python
class Solution:
    def addTwoNumbers(self, l1, l2):
        dummy = ListNode(0)
        current = dummy
        carry = 0
        
        while l1 or l2 or carry:
            val1 = l1.val if l1 else 0
            val2 = l2.val if l2 else 0
            total = val1 + val2 + carry
            carry = total // 10
            current.next = ListNode(total % 10)
            current = current.next
            if l1:
                l1 = l1.next
            if l2:
                l2 = l2.next
        
        return dummy.next
```

### Complexities
---------------------------------
- **Time: O(max(m, n))** — Single pass through both lists, processing each node once
- **Space: O(max(m, n))** — Result list has at most max(m, n) + 1 nodes (if there's a final carry)

