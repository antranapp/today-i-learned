---
title: 849. Maximize Distance to Closest Person
createdAt: 2022-04-05T22:07:23Z
tags: leetcode, algorithm, array
---

# 849. Maximize Distance to Closest Person

**Question Link**: https://leetcode.com/problems/maximize-distance-to-closest-person/

**Difficulty**: Medium

**Additional Info**:
    - https://github.com/103style/LeetCode/blob/master/Array/849.%20Maximize%20Distance%20to%20Closest%20Person.md
    - https://massivealgorithms.blogspot.com/2018/11/leetcode-849-maximize-distance-to.html

```swift
class Solution {
    /// **Primary idea**: Calculate and compare middle point between two taken seats.
    /// **Time Complexity**: O(n)
    /// **Space Complexity**: O(1)
    func maxDistToClosest(_ seats: [Int]) -> Int {
        var lastOne = -1 // Tracking the last person found from left to right
        var maxDistance = 0
        
        for (i, seat) in seats.enumerated() {
            if seat == 1 {
                if lastOne == -1 {
                    maxDistance = max(maxDistance, i) // save the max distance to the last person from the left
                } else {
                    maxDistance = max(maxDistance, (i - lastOne) / 2) // save the max distance between two taken seats
                }
                                      
                lastOne = i
            }
        }
                                      
        // Edge case: only one sitting person
        maxDistance = max(maxDistance, seats.count - lastOne - 1)
        
        return maxDistance
    }
    
    /// **Primary idea**:
    /// Keep track of prev, the filled seat at or to the left of i, and future, the filled seat at or to the right of i.
    /// Then at seat i, the closest person is min(i - prev, future - i), with one exception. i - prev should be considered infinite
    /// if there is no person to the left of seat i, and similarly future - i is infinite if there is no one to the right of seat i.
    /// **Time Complexity**: O(n)
    /// **Space Complexity**: O(1)
    func maxDistToClosest2Points(_ seats: [Int]) -> Int {
        let N = seats.count
        var prev = -1, future = 0
        var ans = 0
        
        for (i, seat) in seats.enumerated() {
            if seat == 1 {
                prev = i
            } else {
                while (future < N && seats[future] == 0 || future < i) {
                    future += 1
                }
                
                let left = prev == -1 ? N : i - prev
                let right = future == N ? N : future - i
                
                ans = max(ans, min(left, right))
            }
        }
        
        return ans
    }
    
    /// **Primary idea**: Track the max consecutive 0, compare the distance of the middle points of these 0 serie to the last sitting person
    /// **Time Complexity**: O(n)
    /// **Space Complexity**: O(1)
    func maxDistToClosestMiddlePoint(_ seats: [Int]) -> Int {
        var i = 0
        var edge = -1
        var count = 0
        var middle = 0
        
        while i < seats.count {
            if seats[i] == 0 {
                i += 1
                count += 1
                if i == seats.count {
                    edge = max(edge, count)
                }
            } else {
                if edge == -1 {
                    edge = count
                } else {
                    middle = max(middle, count)
                }
                count = 0
                i += 1
            }
        }
        
        return (middle + 1) / 2 > edge ? (middle + 1) / 2 : edge
    }
}

let solution = Solution()
solution.maxDistToClosest([1,0,0,0])
solution.maxDistToClosest([0,1])

solution.maxDistToClosest2Points([1,0,0,0])
solution.maxDistToClosest2Points([0,1])


solution.maxDistToClosestMiddlePoint([1,0,0,0])
solution.maxDistToClosestMiddlePoint([0,1])
```