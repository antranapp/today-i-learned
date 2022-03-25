---
title: 350. Intersection of Two Arrays II
createdAt: 2022-03-25T21:40:08Z
tags: leetcode, algorithm, array
---

# 350. Intersection of Two Arrays II

**Question Link**: https://leetcode.com/problems/intersection-of-two-arrays-ii/

**Difficulty**: Easy

```swift
class Solution {
    /// **Primary idea**: Use dictionary to get frequencies of elements of one array, and
    /// compare with another array to filter the intersection
    /// **Time Complexity**: O(n)
    /// **Space Complexity**: O(n)
    func intersection(_ nums1: [Int], _ nums2: [Int]) -> [Int] {
        // Dictionary holding frequences of a number in nums1 array as value, and the number as key
        var numsFreq = Dictionary(nums1.map {($0, 1)}, uniquingKeysWith: +)
        var result = [Int]()
        
        for num in nums2 {
            // Add the num into result only when it is founded in nums1
            // and the frequence value is not exhausted
            if let freq = numsFreq[num], freq > 0 {
                result.append(num)
                
                // Reduce the frequency of the num in the dictionary
                numsFreq[num] = freq - 1
            }
        }
        
        return result
    }
}

let solution = Solution()
solution.intersection([1,2,2,1], [2,2])
```
