---
title: 219. Contains Duplicate II
createdAt: 2022-03-25T22:10:24Z
tags: leetcode, algorithm, array
---

# 219. Contains Duplicate II

**Question** Link: https://leetcode.com/problems/contains-duplicate-ii/

**Dificulty**: Easy

```swift
class Solution {
    /// **Primary idea**: use a dictionary to check duplicates, then judge if their distance is less than k
    /// **Time Complexity**: O(n)
    /// **Space Complexity**: O(n)
    func containsNearbyDuplicate(_ nums: [Int], _ k: Int) -> Bool {
        var dict = [Int: Int]()
        for (i, num) in nums.enumerated() {
            if let j = dict[num], abs(i-j)<=k {
                return true
            }
            dict[num] = i
        }
        
        return false
    }
}

let solution = Solution()
solution.containsNearbyDuplicate([1,2,3,1], 3)
solution.containsNearbyDuplicate([1,0,1,1], 1)
solution.containsNearbyDuplicate([1,2,3,1,2,3], 2)
```