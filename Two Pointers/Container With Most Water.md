## Problem
You are given an integer array `heights` where `heights[i]` represents the height of the $i^{th}$ bar.

You may choose any two bars to form a container. Return the _maximum_ amount of water a container can store.

## Example
```python
Input: height = [1,7,2,5,4,7,3,6]

Output: 36
```

## Solution
```python
class Solution:
    def maxArea(self, heights: List[int]) -> int:
        amount = 0
        bar1 = 0
        bar2 = len(heights) - 1

        while bar1 < bar2:
            length = bar2 - bar1
            height = min(heights[bar2], heights[bar1])
            area = length * height
            
            amount = area if area > amount else amount
            
            if heights[bar1] < heights[bar2]:
                bar1 += 1
            elif heights[bar1] > heights[bar2]:
                bar2 -= 1
            else:
                bar1 += 1
                bar2 -= 1
        
        return amount
```

Explain: