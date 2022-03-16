---
title: 46. Permutations
createdAt: 2022-03-16T22:05:25Z
tags: leetcode, algorithm, depth-first-search
---

# 46. Permutations

```swift
class Solution {
    func permute(_ nums: [Int]) -> [[Int]] {
        // Variable holding the result array
        var result = [[Int]]()
        
        // Variable holding path of visiting numbers
        var path = [Int]()
        
        // Variable marking visited number in nums array.
        var isVisited = [Bool](repeating: false, count: nums.count)
        
        dfs(&result, &path, &isVisited, nums)
        
        return result
    }

    private func dfs(_ result: inout [[Int]], _ path: inout [Int], _ isVisited: inout [Bool], _ nums: [Int]) {
        
        // Append the path array into the result array
        // when we reach the end of the current path
        guard path.count != nums.count else {
            result.append(path)
            return
        }
        
        // Iterate through all unvisited numbers
        for (i, num) in nums.enumerated() where !isVisited[i] {
            // Add the current number to path
            path.append(num)
            // Mark it as visited
            isVisited[i] = true
            // Go deeper into the path to visit the next number
            dfs(&result, &path, &isVisited, nums)
            
            // Reset visiting status of the current number
            // And remove it from path
            // to prepare to visit another branch.
            isVisited[i] = false
            path.removeLast()
        }
    }
}

let solution = Solution()
solution.permute([1,2,3])
```