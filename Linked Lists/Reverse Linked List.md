## Problem


## Example


## Solution
```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next

class Solution:
    def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:
        p1, p2, p3 = None, head, head
        while p3 != None:
            p3 = p3.next
            p2.next = p1
            p1 = p2
            p2 = p3
        return p1
```

Explain: