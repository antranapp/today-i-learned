---
title: 217. Contains Duplicate
createdAt: 2022-03-25T22:05:28Z
tags: leetcode, algorithm, array
---

# 217. Contains Duplicate

**Question Link**: https://leetcode.com/problems/contains-duplicate/

**Difficulty**: Easy

```swift
class Solution {
    /// **Primary idea**: Use hash table to store number frequency
    /// **Time Complexity**: O(n)
    /// **Space Complexity**: O(n)
    func containsDuplicate(_ nums: [Int]) -> Bool {
        var dict = [Int: Int]()
        for num in nums {
            if dict[num] != nil {
                return true
            }
            dict[num] = 1
        }
        
        return false
    }
    
    /// **Primary idea**: traverse the array and use a set to check duplicates
    /// **Time Complexity**: O(n)
    /// **Space Complexity**: O(n)
    func containsDuplicate2(nums: [Int]) -> Bool {
        return nums.count > Set(nums).count
    }
}

let solution = Solution()
solution.containsDuplicate([1,2,3,1])
solution.containsDuplicate([1,2,3,4])
```