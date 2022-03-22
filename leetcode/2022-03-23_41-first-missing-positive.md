---
title: 41. First Missing Positive
createdAt: 2022-03-22T21:59:38Z
tags: leetcode, algorithm, array
---

# 41. First Missing Positive


**Question Link**: https://leetcode.com/problems/first-missing-positive/

**Difficulty**: Hard

**Further Information**: https://www.geeksforgeeks.org/find-the-smallest-positive-number-missing-from-an-unsorted-array/

```swift
class Solution {
    // Primary idea: Use a set to hold number in the array and iterate through 1...nums.count to find the missing one
    // Time Complexity: O(n)
    // Space Complexity: O(n)
    func firstMissingPositiveUsingSet(_ nums: [Int]) -> Int {
        let numSet = Set(nums)
        for i in 0..<nums.count {
            if !numSet.contains(i + 1) {
                return i + 1
            }
        }
        
        return nums.count + 1
    }
}

let solution = Solution()
solution.firstMissingPositiveUsingSet([1,2,0])
solution.firstMissingPositiveUsingSet([3,4,-1,1])
solution.firstMissingPositiveUsingSet([7,8,9,11,12])
```