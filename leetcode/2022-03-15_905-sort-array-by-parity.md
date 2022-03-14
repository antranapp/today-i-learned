---
title: 905. Sort Array By Parity
createdAt: 2022-03-14T23:03:47Z
tags: leetcode, algorithm, array
---

# 905. Sort Array By Parity

**Problem**: [905. Sort Array By Parity](https://leetcode.com/problems/sort-array-by-parity/)

**Primary idea**: traverse the array and insert Even into the 0 th index and odd into the last index

**Difficulty**: Easy

**Time Complexity**: O(n)

**Space Complexity**: O(n)

## Swift

```swift
class Solution {
    func sortArrayByParity(_ nums: [Int]) -> [Int] {
        // Array holding the result
        var result = [Int]()
        
        // Iterate over the nums array
        // Insert even numbers at the leading position of the result array
        // Insert odd numbers at the trailing position of the result array
        for num in nums.enumerated() {
            result.insert(num.element, at: num.element.isMultiple(of: 2) ? 0 : result.count)
        }
        
        return result
    }
}

let solution = Solution()
solution.sortArrayByParity([3,1,2,4])
solution.sortArrayByParity([0])
```
