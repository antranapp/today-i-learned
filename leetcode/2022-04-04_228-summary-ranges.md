---
title: 228. Summary Ranges
createdAt: 2022-04-03T22:59:10Z
---

# 228. Summary Ranges

 **Question Link**: https://leetcode.com/problems/summary-ranges/

 **Difficulty**: Easy

 
```swift
/// **Primary idea**: Traverse the array and build string when num[i] != num[i - 1] + 1, 
/// note to handle the edge case when it goes to the end of the array
/// **Time Complexity**: O(n) 
/// **Space Complexity**: O(n)
class Solution {
    func summaryRanges(_ nums: [Int]) -> [String] {
        var results = [String]()
        
        var str = ""
        var start = 0
        
        guard nums.count > 0 else {
            return results
        }
        
        for i in 0...nums.count {
            if i == nums.count || (i > 0 && nums[i] != nums[i - 1] + 1) {
                str = "\(nums[start])"
                if i - 1 != start {
                    str += "->\(nums[i - 1])"
                }
                results.append(str)
                start = i
            }
            
        }
        
        return results
    }
}

let solution = Solution()
solution.summaryRanges([0,1,2,4,5,7])
```