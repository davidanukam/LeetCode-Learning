## Solution
```python
class Solution:
    def longestConsecutive(self, nums: List[int]) -> int:
        nums = list((sorted(list(set(nums)))))
        
        ans = 0
        prev = 0

        if len(nums) == 0: return 0
        if len(nums) == 1: return 1

        for i in range(len(nums) - 1):
            if i == 0: ans += 1
            if nums[i + 1] - nums[i] == 1:
                ans += 1
            else:
                if ans > prev:
                    prev = ans
                ans = 1

        return prev if prev > ans else ans

```

