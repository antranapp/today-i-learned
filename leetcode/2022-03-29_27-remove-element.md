---
title: 27. Remove Element
createdAt: 2022-03-28T22:19:16Z
tags: leetcode, algorithm, array
---

# 27. Remove Element

**Question Link**: https://leetcode.com/problems/remove-element/

**Difficulty**: Easy

```swift
// **Primary idea**: keep a index, compare the element at that index with val while moving forward
// **Time Complexity**: O(n)
// **Space Complexity**: O(1)
class Solution {
    func removeElement(_ nums: inout [Int], _ val: Int) -> Int {
        var noneZeroIndex = 0
        
        // Iterate through the array, update the noneZeroIndex
        for num in nums where num != val {
            nums[noneZeroIndex] = num
            noneZeroIndex += 1
        }
        
        return noneZeroIndex
    }
}

let solution = Solution()
var input1 = [3,2,2,3]
let result1 = solution.removeElement(&input1, 3)
print(input1[0..<result1])

var input2 = [3,2,2,3]
let result2 = solution.removeElement(&input2, 2)
print(input2[0..<result2])

var input3 = [0]
let result3 = solution.removeElement(&input3, 0)
print(input3[0..<result3])
```