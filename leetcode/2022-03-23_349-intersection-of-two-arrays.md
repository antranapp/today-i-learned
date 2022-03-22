---
title: 349. Intersection of Two Arrays
createdAt: 2022-03-22T22:32:22Z
tags: leetcode, algorithm, array
---

# 349. Intersection of Two Arrays

**Question Link**: https://leetcode.com/problems/intersection-of-two-arrays/

**Difficulty**: Easy

```swift
// Primary idea: Use set to hold numbers for one array and iterate the other one to output result, 
// remove the number from set to avoid duplicates.
// Note: Do not use built-in intersection function for Set in Swift, that is not this question is asking for.
// Time Complexity: O(n) 
// Space Complexity: O(n)
class Solution {
    func intersection(_ nums1: [Int], _ nums2: [Int]) -> [Int] {
        // Convert nums1 to Set to ensure there is 
        // no dupplication in nums1
        var nums1Set = Set(nums1)

        var result = [Int]()
        
        for num in nums2 where nums1Set.contains(num) {
            result.append(num)
            // Remove the number from nums1Set
            // to ensure we don't add dupplicated value into the
            // result array
            nums1Set.remove(num)
        }
        
        return result
    }
}

let solution = Solution()
solution.intersection([1,2,2,1], [2,2])
```