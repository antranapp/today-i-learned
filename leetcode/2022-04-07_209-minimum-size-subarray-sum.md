---
title: 209. Minimum Size Subarray Sum
createdAt: 2022-04-06T22:11:46Z
tags: leetcode, algorithm, array
---

# 209. Minimum Size Subarray Sum

**Question Link:** https://leetcode.com/problems/minimum-size-subarray-sum/

**Difficulty:**  Medium

**Additional Info:** https://www.geeksforgeeks.org/find-subarray-with-given-sum/

```swift
class Solution {
    /// **Primary idea:** Two Pointers, anchor the former and move forward the latter one to ensure the sum of subarray just covers the target
    /// **Time Complexity:** O(n)
    /// **Space Complexity:** O(1).
    func minSubArrayLen(_ target: Int, _ nums: [Int]) -> Int {
        var minSize = Int.max
        var start = 0
        var currentSum = 0
        
        // Add elements one by one to currentSum,
        // and if currentSum exceeds the target sum,
        // then remove the starting element
        for (i, num) in nums.enumerated() {
            currentSum += num
            
            // if the currentSum exceeds the target sum, save the minSize value
            // and remove the starting element from currentSum
            while currentSum >= target, start <= i {
                minSize = min(minSize, i - start + 1)
                
                currentSum -= nums[start]
                start += 1
            }
        }
        
        return minSize == Int.max ? 0 : minSize
    }
}

let solution = Solution()
solution.minSubArrayLen(7, [2,3,1,2,4,3])
solution.minSubArrayLen(4, [1,4,4])
solution.minSubArrayLen(1, [1,1,1,1,1,1,1,1])
```