---
title: 243. Shortest Word Distance
createdAt: 2022-04-06T22:03:46Z
tags: leetcode, algorithm, array
---

# 243. Shortest Word Distance

Given a list of words and two wordsword1_and_word2, return the shortest distance between these two words in the list.

**Example:**

Assume that words =["practice", "makes", "perfect", "coding", "makes"].

```
Input: word1 = “coding”, word2 = “practice”
Output: 3
```

```
Input: word1 = "makes", word2 = "coding"
Output: 1
```

**Note:**
You may assume that word1 does not equal to word2, and _word1 _and _word2 _are both in the list.

**Question Link:** https://leetcode.com/problems/shortest-word-distance/

**Difficulty:** Easy

**Additional Info:**
    - https://aaronice.gitbook.io/lintcode/hash-table/shortest-word-distance

```swift
class Solution {
    /// **Primary idea**: Iterate and update index and distance when encounter word1 or word2
    /// **Time Complexity**: O(n)
    /// **Space Complexity**: O(1)
    func shortestDistance(_ words: [String], _ word1: String, _ word2: String) -> Int {
        var shortest = Int.max
        var i1 = -1, i2 = -1
        for (i, word) in words.enumerated() {
            if word == word1 {
                i1 = i
            }
            
            if word == word2 {
                i2 = i
            }
            
            if i1 != -1 && i2 != -1 {
                shortest = min(abs(i1-i2), shortest)
            }
        }
        
        return shortest
    }
}

let solution = Solution()
solution.shortestDistance(["practice", "makes", "perfect", "coding", "makes"], "coding", "practice")
solution.shortestDistance(["practice", "makes", "perfect", "coding", "makes"], "makes", "coding")
```