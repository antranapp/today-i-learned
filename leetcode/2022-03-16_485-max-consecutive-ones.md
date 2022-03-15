---
title: 485. Max Consecutive Ones
createdAt: 2022-03-15T21:53:16Z
tags: leetcode, algorithm, array
---

# 485. Max Consecutive Ones

**Problem**: [485. Max Consecutive Ones](https://leetcode.com/problems/max-consecutive-ones/)

**Difficulty**: Easy

**Time Complexity**: O(n)

**Space Complexity**: O(1)

```swift
class Solution {
    func findMaxConsecutiveOnes(_ nums: [Int]) -> Int {
        // Variable holding the global counter
        var globalMax = 0
        
        // Variable holding the local counter
        var localMax = 0
        
        // Iterate through all number
        for num in nums {
            
            if num == 1 {
                // Increase local counter and
                // Update global counter if needed
                localMax += 1
                globalMax = max(globalMax, localMax)
            } else {
                // Reset local counter
                localMax = 0
            }
        }
        
        return globalMax
    }
}

let solution = Solution()
solution.findMaxConsecutiveOnes([1,1,0,1,1,1])
solution.findMaxConsecutiveOnes([0])
solution.findMaxConsecutiveOnes([1])
solution.findMaxConsecutiveOnes([])
```
