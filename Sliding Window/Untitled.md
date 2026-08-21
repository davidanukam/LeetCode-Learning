## Problem


## Example


## Solution
```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        bp = prices[0]
        sp = prices[0]
        profit = sp - bp
        
        for i in range(1, len(prices)):
            if prices[i] < bp:j
                bp = prices[i]
                sp = prices[i]
            elif prices[i] > sp:
                sp = prices[i]
            profit = max(profit, sp - bp)
        
        return profit
```

Explain: