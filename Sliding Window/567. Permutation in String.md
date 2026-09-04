## Problem
You are given two strings `s1` and `s2`.

Return `true` if `s2` contains a permutation of `s1`, or `false` otherwise. That means if a permutation of `s1` exists as a substring of `s2`, then return `true`.

Both strings only contain lowercase letters.

## Example
```python
Input: s1 = "abc", s2 = "lecabee"

Output: true
```

## Solution
```python
class Solution:
    def checkInclusion(self, s1: str, s2: str) -> bool:
        w = len(s1)

        count1 = {}

        for letter in s1:
            count1[letter] = 1 + count1.get(letter, 0)
        
        count2 = {}

        l = 0
        for r in range(len(s2)):
            found = True
            count2[s2[r]] = 1 + count2.get(s2[r], 0)
            if r - l + 1 == w:
                for key, value in count2.items():
                    if key not in count1:
                        found = False
                        break
                    else:
                        if value != count1[key]:
                            found = False
                            break
                if found:
                    return True
                else:
                    # Not a permutation
                    if count2[s2[l]] - 1 == 0:
                        count2.pop(s2[l], None)
                    else:
                        count2[s2[l]] -= 1
                    l += 1
        
        return False
```

Explain: