---
title: 5. Longest Palindromic Substring
createdAt: 2022-03-19T22:12:17Z
tags: leetcode, algorithm, string
---

# 5. Longest Palindromic Substring

**Question Link**: https://leetcode.com/problems/longest-palindromic-substring/

**Primary idea**: Find the longest palindrome string from every index at the center.

**Time Complexity**: O(n^2): Outer Loop that traverse through entire string, and Inner Loop that is used to expend from i .

**Space Complexity**: O(1): No extra space is needed.

**Further Info**: https://www.geeksforgeeks.org/longest-palindromic-substring-set-2/

```swift
class Solution {
    func longestPalindrome(_ s: String) -> String {
        guard s.count > 1 else {
            return s
        }
        
        let characters = Array(s)
        var maxLength = 0, start = 0
        
        for i in 0..<characters.count {
            searchPalindrome(characters, i, i, &start, &maxLength)
            searchPalindrome(characters, i, i+1, &start, &maxLength)
        }
        
        return String(characters[start ..< start+maxLength])
    }
    
    private func searchPalindrome(_ characters: [Character], _ leftIndex: Int, _ rightIndex: Int, _ startIndex: inout Int, _ maxLength: inout Int) {
        var leftIndex = leftIndex, rightIndex = rightIndex

        while leftIndex >= 0, rightIndex < characters.count, characters[leftIndex] == characters[rightIndex] {
            leftIndex -= 1
            rightIndex += 1
        }
        
        let length = rightIndex - leftIndex - 1
        if maxLength < length {
            startIndex = leftIndex + 1
            maxLength = length
        }
    }
}

let solution = Solution()
solution.longestPalindrome("bab")
solution.longestPalindrome("babad")
solution.longestPalindrome("cbbd")
solution.longestPalindrome("forgeeksskeegfor")
```