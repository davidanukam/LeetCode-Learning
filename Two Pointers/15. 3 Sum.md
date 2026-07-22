## Problem
Given an integer array `nums`, return all the triplets `[nums[i], nums[j], nums[k]]` where `nums[i] + nums[j] + nums[k] == 0`, and the indices `i`, `j` and `k` are all distinct.

The output should _not_ contain any duplicate triplets. You may return the output and the triplets in **any order**.

## Example
```python
Input: nums = [-1,0,1,2,-1,-4]

Output: [[-1,-1,2],[-1,0,1]]
```

## Solution
```python
class Solution:
    def threeSum(self, nums: List[int]) -> List[List[int]]:
        nums = list(sorted(nums))
        output = []
  
        for i in range(len(nums)):
            target = nums[i]
            p1 = 0
            p2 = len(nums) - 1

            while p1 < p2:
                if p1 == i:
                    p1 += 1
                    continue
                if p2 == i:
                    p2 -= 1
                    continue
                if nums[p1] + nums[p2] == -target:
                    triplet = list(sorted([nums[p1], nums[p2], target]))
                    if triplet not in output:
                        output.append(triplet)
                    p1 += 1
                    p2 -= 1
                elif nums[p1] + nums[p2] < -target:
                    p1 += 1
                elif nums[p1] + nums[p2] > -target:
                    p2 -= 1
        
        return output
```

Explain: