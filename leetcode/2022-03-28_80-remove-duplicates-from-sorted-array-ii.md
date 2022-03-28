---
title: 80. Remove Duplicates from Sorted Array II
createdAt: 2022-03-27T22:02:53Z
tags: leetcode, algorithm, array
---

# 80. Remove Duplicates from Sorted Array II

**Question Link**: https://leetcode.com/problems/remove-duplicates-from-sorted-array-ii/
**Difficulty**: Medium

```swift

class Solution {
    /// **Primary idea**: keep a index, compare between the element at that index, the element at index - 1, 
    /// and the element moving forward
    /// **Time Complexity**: O(n) 
    /// **Space Complexity**: O(1)
    func removeDuplicates(_ nums: inout [Int]) -> Int {
        guard nums.count > 2 else {
            return nums.count
        }

        var index = 1
        
        for i in 2..<nums.count {
            if nums[index] != nums[index - 1] || nums[index] != nums[i] {
                index += 1
                nums[index] = nums[i]
            }
        }
        
        return index + 1
    }
}

let solution = Solution()
var input1 = [1,1,1,2,2,3]
let result1 = solution.removeDuplicates(&input1)
print(input1[0..<result1])

var input2 = [0,0,1,1,1,1,2,3,3]
let result2 = solution.removeDuplicates(&input2)
print(input2[0..<result2])

var input3: [Int] = []
let result3 = solution.removeDuplicates(&input3)
print(input3[0..<result3])

var input4 = [1]
let result4 = solution.removeDuplicates(&input4)
print(input4[0..<result4])
```
