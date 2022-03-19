---
title: 3. Longest Substring Without Repeating Characters
createdAt: 2022-03-17T23:32:05Z
tags: leetcode, algorithm, string
---

# 3. Longest Substring Without Repeating Characters

**Question Link**: https://leetcode.com/problems/longest-substring-without-repeating-characters/

**Primary idea**: Use a dictionary to hold the next possible valid position of characters of the non-repeating substring,  and then iterate the string to update maxLen, dictionary, and startIdx encountering duplicates
 
**Time Complexity**: O(n)
 
**Space Complexity**: O(n)

**Further info**: https://www.geeksforgeeks.org/length-of-the-longest-substring-without-repeating-characters/

```swift
class Solution {
    func lengthOfLongestSubstring(_ s: String) -> Int {
        
        // Max possible length of non-repeating string
        var maxLen = 0
        
        // starting the initial point of window to index 0
        var startIdx = 0
        
        // Dictionary with key = character, and value = index of the next possible valid position of the character in a non-repeating string
        var charToPos = [Character: Int]()
        
        // Convert the string into array of characters for processing
        let characters = Array(s)
        
        for (i, character) in characters.enumerated() {
            // Checking if we have already seen the element or not
            if let pos = charToPos[character] {
                // If we have seen the number, move the start pointer
                // to position after the last occurrence
                startIdx = max(startIdx, pos + 1)
            }
            
            // Updating the last seen value of the character
            charToPos[character] = i
            
            // Update the maxLen considering the length of the current non-repeating string window
            maxLen = max(maxLen, i - startIdx + 1)
        }
        
        return maxLen
    }
}

let solution = Solution()
solution.lengthOfLongestSubstring("abcabcbb")
solution.lengthOfLongestSubstring("bbbbb")
solution.lengthOfLongestSubstring("abbbbb")
solution.lengthOfLongestSubstring("pwwkew")
```