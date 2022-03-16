---
title: 47. Permutations II
createdAt: 2022-03-16T22:37:58Z
tags: leetcode, algorithm, depth-first-search
---

# 47. Permutations II

**Question Link**: https://leetcode.com/problems/permutations-ii/

**Difficulty**: Medium

**Primary idea**: Classic Depth-first Search, adopt last occurrence to avoid dupliates

**Time Complexity**: O(n^n) 

**Space Complexity**: O(n)

```swift
class Solution {
    func permute(_ nums: [Int]) -> [[Int]] {
        // Variable holding the result array
        var result = [[Int]]()
        
        // Variable holding path of visiting numbers
        var path = [Int]()
        
        // Variable marking visited number in nums array.
        var isVisited = [Bool](repeating: false, count: nums.count)
        
        let nums = nums.sorted(by: <)
        
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
        
        for i in 0..<nums.count {
            // Skip processing if the current num is visited
            // Or the current num is equal the last visited num.
            if isVisited[i] || (i > 0 && nums[i] == nums[i - 1] && isVisited[i - 1]) {
                continue
            }
            
            // Add the current number to path
            path.append(nums[i])
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
solution.permute([1,1,2])
solution.permute([1,2,3])
```