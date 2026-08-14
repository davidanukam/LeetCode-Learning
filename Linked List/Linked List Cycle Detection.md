## Problem


## Example
![[Pasted image 20260813214856.png]]

```java
Input: head = [1,2,3,4], index = 1

Output: true
```

## Solution
```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next

class Solution:
    def hasCycle(self, head: Optional[ListNode]) -> bool:
        seen = []
        curr = head
        while curr != None:
            if curr in seen:
                return True
            else:
                seen.append(curr)
                curr = curr.next
        return False
```

Explain: 