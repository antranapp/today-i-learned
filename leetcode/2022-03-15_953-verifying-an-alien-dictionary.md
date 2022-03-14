---
title: 953. Verifying an Alien Dictionary
createdAt: 2022-03-14T22:41:48Z
tags: leetcode, algorithm, array
---

# 953. Verifying an Alien Dictionary

**Problem:** [Verify an Alien Dictionary](https://leetcode.com/problems/verifying-an-alien-dictionary/)

**Primary idea**: Compare words one by one and make sure they are following the order

**Difficulty:** Easy

**Time Complexity:** O(n)

**Space Complexity:** O(n)

## Swift

```swift
class Solution {
    func isAlienSorted(_ words: [String], _ order: String) -> Bool {
        // Use Hastable data structure to map character to position from the order string.
        // Convert order string into a dictionary
        // where key = the position of the character in the order string
        // and value = the character.
        // This is used to quickly look up for the position of a character
        // when we iterate over the characters in words later.
        let charToOrder = Dictionary(uniqueKeysWithValues: order.enumerated().map { ($0.1, $0.0) })
        
        for i in 0 ..< words.count - 1 {
            let currentWord = Array(words[i])
            let nextWord = Array(words[i + 1])
            
            // Interate over all characters of both words to compare
            // the possitions of the corresponding characters
            // Stop when one of the word ends, or the orders of characters are not valid
            var j = 0
            while j < min(currentWord.count, nextWord.count) {
                let currentChar = currentWord[j], nextChar = nextWord[j]
                
                // Go to the next position if the current characters
                // of both words are the same, since it's valid.
                guard currentChar != nextChar else {
                    j += 1
                    continue
                }
                
                if charToOrder[currentChar]! > charToOrder[nextChar]! {
                    // Stop when the orders are invalid
                    return false
                } else {
                    // The orders are valid, stop the loop for the current word pair
                    break
                }
            }
            
            // Edge case: "apple" vs. "app"; "kuvp" vs. "q"
            if j == nextWord.count && currentWord.count > nextWord.count {
                return false
            }
        }
        
        return true
    }
}
```