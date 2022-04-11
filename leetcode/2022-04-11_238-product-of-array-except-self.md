---
title: 238. Product of Array Except Self
createdAt: 2022-04-10T22:16:24Z
tags: leetcode, algorithm, array
---

# 238. Product of Array Except Self

**Question Link**: https://leetcode.com/problems/product-of-array-except-self/

**Difficulty**: Medium

**Additional info**: https://www.geeksforgeeks.org/a-product-array-puzzle/
    - 

```swift
class Solution {
    /// Primary idea: Dynamic Programming, track Left and Right product lists at the same time and just use one additional array. The problem statement mentions that using theanswer array doesn't add to the space complexity.
    /// Time Complexity: O(n)
    /// Space Complexity: O(1)
    func productExceptSelf(_ nums: [Int]) -> [Int] {
        // Allocate memory for the product array
        // Initialize the product array as 1
        var arr = Array.init(repeating: 1, count: nums.count)
        
        // Calculate the products of elements on the right side excluding arr[i]
        for i in (0..<(nums.count - 1)).reversed() {
            arr[i] = arr[i+1] * nums[i+1]
        }
        
        // Calculate the products of elements on the left side excluding arr[i]
        var left = 1
        for i in 0..<nums.count {
            if i == 0 {
                arr[i] = left * arr[i]
            } else {
                left = left * nums[i-1]
                arr[i] = left * arr[i]
            }
        }
        
        return arr
    }
}

let solution = Solution()
solution.productExceptSelf([1,2,3,4])
solution.productExceptSelf([-1,1,0,-3,3])
solution.productExceptSelf([3])
```