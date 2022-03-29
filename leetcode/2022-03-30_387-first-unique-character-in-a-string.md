---
title: 387. First Unique Character in a String
createdAt: 2022-03-29T23:00:36Z
tags: leetcode, algorithm, string
---

# 387. First Unique Character in a String

**Question Link**: https://leetcode.com/problems/first-unique-character-in-a-string/
**Difficulty**: Easy

```swift
class Solution {
    /// **Primary idea**: Keep track of existence of each character in the string
    /// **Time Complexity**: O(n)
    /// **Space Complexity**: O(1): The maximum space of the dictionary is 26, so space complexity is O(1)
    func firstUniqChar(_ s: String) -> Int {
        var occurences = [Character: Bool]()
        let characters = Array(s)
        
        for char in characters {
            if occurences[char] != nil {
                occurences[char] = true
            } else {
                occurences[char] = false
            }
        }
        
        for (i, char) in characters.enumerated() {
            if !occurences[char]! {
                return i
            }
        }
        
        return -1
    }
}

let solution = Solution()
solution.firstUniqChar("leetcode")
solution.firstUniqChar("loveleetcode")
solution.firstUniqChar("aabb")
solution.firstUniqChar("aadadaad")
```