---
title: 54. Spiral Matrix
createdAt: 2022-04-11T22:15:03Z
tags: leetcode, algorithm, array
---

# 54. Spiral Matrix

**Question Link**: https://leetcode.com/problems/spiral-matrix/

**Difficulty**: Medium

```swift
class Solution {
    /// Primary idea: Use four index to get the right element during iteration
    /// Time Complexity: O(n^2)
    /// Space Complexity: O(1)    
    func spiralOrder(_ matrix: [[Int]]) -> [Int] {
        var result = [Int]()
        
        guard matrix.count > 0 else {
            return result
        }
        
        var startX = 0
        var endX = matrix.count - 1
        var startY = 0
        var endY = matrix[0].count - 1
        
        while true {
            // top
            for i in startY...endY {
                result.append(matrix[startX][i])
            }
            startX += 1
            if startX > endX {
                break
            }
            
            // right
            for i in startX...endX {
                result.append(matrix[i][endY])
            }
            endY -= 1
            if startY > endY {
                break
            }
            
            // bottom
            for i in stride(from: endY, through: startY, by: -1) {
                result.append(matrix[endX][i])
            }
            endX -= 1
            if startX > endX {
                break
            }
            
            // left
            for i in stride(from: endX, through: startX, by: -1) {
                result.append(matrix[i][startY])
            }
            startY += 1
            if startY > endY {
                break
            }
        }
        
        return result
    }
}

let solution = Solution()
solution.spiralOrder([[1,2,3],[4,5,6],[7,8,9]])
solution.spiralOrder([[1,2,3,4],[5,6,7,8],[9,10,11,12]])
```