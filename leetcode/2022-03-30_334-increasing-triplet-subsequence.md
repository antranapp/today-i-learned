---
title: 334. Increasing Triplet Subsequence
createdAt: 2022-03-29T22:45:49Z
tags: leetcode, algorithm, array
---

# 334. Increasing Triplet Subsequence

**Question Link**: https://leetcode.com/problems/increasing-triplet-subsequence/

**Difficulty**: Medium

```swift
class Solution {
    /// **Primary idea**: Two pointers. One is to store the smallest value,
    /// the other is to store the second smallest value.
    /// Return true once find a value greater than both.
    /// **Time Complexity: O(n)
    /// **Space Complexity: O(1)
    func increasingTriplet(_ nums: [Int]) -> Bool {
        var smallest = Int.max, secondSmallest = Int.max
        
        for num in nums {
            if smallest >= num {
                smallest = num
            } else if secondSmallest >= num {
                secondSmallest = num
            } else {
                return true
            }
        }
        
        return false
    }
}

let solution = Solution()
solution.increasingTriplet([1,2,3,4,5])
solution.increasingTriplet([5,4,3,2,1])
solution.increasingTriplet([2,1,5,0,4,6])
```