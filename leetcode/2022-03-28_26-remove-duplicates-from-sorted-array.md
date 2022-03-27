---
title: 26. Remove Duplicates from Sorted Array
createdAt: 2022-03-27T21:55:25Z
tags: leetcode, algorithm, array
---

# 26. Remove Duplicates from Sorted Array

**Question Link**: https://leetcode.com/problems/remove-duplicates-from-sorted-array/
**Difficulty**: Easy

```swift
/// **Primary idea**: keep a index, compare the element at that index with the element moving forward
/// **Time Complexity**: O(n) 
/// **Space Complexity**: O(1)
class Solution {
    func removeDuplicates(_ nums: inout [Int]) -> Int {
        var index = 0
        
        for num in nums where num != nums[index] {
            index += 1
            nums[index] = num
        }
        
        return index + 1
    }
}

let solution = Solution()
var input1 = [1,1,2]
let result1 = solution.removeDuplicates(&input1)
print(input1[0..<result1])

var input2 = [0,0,1,1,1,2,2,3,3,4]
let result2 = solution.removeDuplicates(&input2)
print(input2[0..<result2])

var input3: [Int] = []
let result3 = solution.removeDuplicates(&input3)
print(input2[0..<result3])
```