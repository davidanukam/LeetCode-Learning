## Problem


## Example


## Solution 1 (getMin is not `O(1)`)
```python
class MinStack:

    def __init__(self):
        self.stack = []
        self.minstack = []

    def push(self, val: int) -> None:
        self.stack.append(val)
        if len(self.minstack):
            if val <= self.minstack[-1]:
                self.minstack.append(val)
        else:
            self.minstack.append(val)

    def pop(self) -> None:
        if len(self.minstack):
            if self.minstack[-1] == self.stack[-1]:
                self.minstack.pop()
        self.stack.pop()

    def top(self) -> int:
        return self.stack[-1]

    def getMin(self) -> int:
        return min(self.stack)
```


## Solution 2
```python
class MinStack:

    def __init__(self):
        self.stack = []
        self.minstack = []

    def push(self, val: int) -> None:
        self.stack.append(val)
        if len(self.minstack):
            if val <= self.minstack[-1]:
                self.minstack.append(val)
        else:
            self.minstack.append(val)

    def pop(self) -> None:
        if len(self.minstack):
            if self.minstack[-1] == self.stack[-1]:
                self.minstack.pop()
        self.stack.pop()

    def top(self) -> int:
        return self.stack[-1]

    def getMin(self) -> int:
        return self.minstack[-1]

```