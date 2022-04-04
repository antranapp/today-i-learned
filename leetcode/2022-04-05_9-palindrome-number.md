---
title: 9. Palindrome Number
createdAt: 2022-04-04T22:19:42Z
tags: leetcode, algorithm, math
---

# 9. Palindrome Number

**Question Link**: https://leetcode.com/problems/palindrome-number/

**Difficulty**: Easy

**Additional Resources**:
    - https://www.code-recipe.com/post/palindrome-number
    - https://walkccc.me/LeetCode/problems/0009/

```swift
class Solution {
    /// **Primary idea**: Calculate the reverted value and compare it with the original value.
    /// **Time Complexity**: O(d): d = number of digits
    /// **Space Complexity**: O(1)
    func isPalindrome(_ x: Int) -> Bool {
        // Special cases:
        // As discussed above, when x < 0, x is not a palindrome.
        // Also if the last digit of the number is 0, in order to be a palindrome,
        // the first digit of the number also needs to be 0.
        // Only 0 satisfy this property.
        if(x < 0 || (x % 10 == 0 && x != 0)) {
            return false;
        }
        
        var revertedNumber = 0
        var y = x
        
        while y > 0 {
            revertedNumber = revertedNumber * 10 + y % 10
            y /= 10
            
            print(revertedNumber, y)
        }
         
        // When the length is an odd number, we can get rid of the middle digit by revertedNumber/10
        // For example when the input is 12321, at the end of the while loop we get x = 12, revertedNumber = 123,
        // since the middle digit doesn't matter in palidrome(it will always equal to itself), we can simply get rid of it.
        return revertedNumber == x || x == revertedNumber/10
    }
}

let solution = Solution()
solution.isPalindrome(121)
solution.isPalindrome(-121)
solution.isPalindrome(10)
```