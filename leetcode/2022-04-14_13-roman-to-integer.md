---
title: 13. Roman to Integer
createdAt: 2022-04-13T21:51:57Z
tags: leetcode, algorithm, array
---

# 13. Roman to Integer

**Question Link**: https://leetcode.com/problems/spiral-matrix-ii/

**Difficulty**: Medium

```swift
class Solution {
    /// Primary idea: Go from clockwise and populate number, remember to handle the center one
    /// Time Complexity: O(n^2)
    /// Space Complexity: O(1)
    func generateMatrix(_ n: Int) -> [[Int]] {
        var num = 1
        var result = Array(repeating: Array(repeating: 0, count: n), count: n)
        
        for layer in 0 ..< n/2 {
            let start = layer
            let end = n - layer - 1
            
            // top
            for i in start ..< end {
                result[start][i] = num
                num += 1
            }
            
            // right
            for i in start ..< end {
                result[i][end] = num
                num += 1
            }
            
            // bottom
            for i in stride(from: end, to: start, by: -1) {
                result[end][i] = num
                num += 1
            }
            
            // left
            for i in stride(from: end, to: start, by: -1) {
                result[i][start] = num
                num += 1
            }
        }

        if n % 2 != 0 {
            result[n/2][n/2] = n*n
        }
        
        return result
    }
}

let solution = Solution()
solution.generateMatrix(3)
solution.generateMatrix(4)
```