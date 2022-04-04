---
title: 735. Asteroid Collision
createdAt: 2022-04-04T22:03:40Z
---

# 735. Asteroid Collision

**Question Link**: https://leetcode.com/problems/asteroid-collision/

**Difficulty**: Medium

**Additional Resources**:
    - https://walkccc.me/LeetCode/problems/0735/
    

```swift
class Solution {
    /// **Primary idea**: Traverse the array and handle positive and negative separately.
    /// **Time Complexity**: O(n)
    /// **Space Complexity**: O(n)
    func asteroidCollision(_ asteroids: [Int]) -> [Int] {
        var positives = [Int]()
        var negatives = [Int]()
        
        for asteroid in asteroids {
            if asteroid > 0 { // positive asteroid
                positives.append(asteroid)
            } else { // negative asteroid
                var shouldAppendToNegative = true
                
                while positives.count > 0 {
                    if positives.last! > -asteroid {
                        // The current asteroid is destroyed
                        shouldAppendToNegative = false
                        break
                    } else {
                        // Last Positive asteroid is destroyed
                        let lastPositive = positives.removeLast()
                        
                        // The current asteroid is destroyed as well
                        if -asteroid == lastPositive {
                            shouldAppendToNegative = false
                        }
                    }
                }
                
                if shouldAppendToNegative {
                    negatives.append(asteroid)
                }
            }
        }
        
        return negatives + positives
    }
    
    /// **Primary idea**:
    ///     - We create a list to store the result res
    ///     - If a new asteroid value is positive, we add to the list as it will never collide with ones in res
    ///     - Else, we remove all the positive asteroids that smaller than the new value (negative)
    ///     - Then add the new value to res if res is empty or the last element is also negative (as it already processed in the previous run)
    ///     - If we have two opposite asteroids of the same size, then remove the last one.
    /// **Time Complexity**: O(n)
    /// **Space Complexity**: O(n)
    func asteroidCollision2(_ asteroids: [Int]) -> [Int] {
        var stack = [Int]()
        
        for asteroid in asteroids {
            if asteroid > 0 {
                stack.append(asteroid)
            } else {
                while !stack.isEmpty && stack.last! > 0 && stack.last! < -asteroid {
                    stack.removeLast()
                }
                
                if stack.isEmpty || stack.last! < 0 {
                    stack.append(asteroid)
                } else if (stack.last! == -asteroid) {
                    stack.removeLast()
                }
            }
        }
        
        return stack
    }
}

let solution = Solution()
solution.asteroidCollision([5,10,-5])
solution.asteroidCollision2([5,10,-5])
```