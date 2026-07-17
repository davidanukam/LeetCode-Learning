## Problem
You are given an array of strings `tokens` that represents a **valid** arithmetic expression in [Reverse Polish Notation](https://en.wikipedia.org/wiki/Reverse_Polish_notation).

Return the integer that represents the evaluation of the expression.

- The operands may be integers or the results of other operations.
- The operators include `'+'`, `'-'`, `'*'`, and `'/'`.
- Assume that division between integers always truncates toward zero.

## Example
```python
Input: tokens = ["1","2","+","3","*","4","-"]

Output: 5

Explanation: ((1 + 2) * 3) - 4 = 5
```

## Solution
```python
class Solution:
    def evalRPN(self, tokens: List[str]) -> int:
        stack = []
        for token in tokens:
            if token.isnumeric():
                stack.append(int(token))
            elif len(token) > 1 and "-" in token:
                stack.append(int(token))
            else:
                num2 = stack.pop()
                num1 = stack.pop()
                if token == "+":
                    stack.append(num1 + num2)
                elif token == "-": 
                    stack.append(num1 - num2)
                elif token == "*": 
                    stack.append(num1 * num2)
                elif token == "/": 
                    stack.append(int(num1 / num2))
        return stack[-1] if len(stack) else 0

```

Using a stack (LIFO $\rightarrow$ Last In First Out), we can compute any equation using the Reverse Polish Notation.

First, we need to make sure we can differentiate between numbers and operators. For each token in the list, we can check if it is a positive or negative number. If it is one of the two, then we can push its value to the stack.

However, if the token is an operator, then we first pop out the top 2 elements on our stack and check what operator the token is. Once we have that, we can evaluate the equation and push the new number back onto the top of the stack.