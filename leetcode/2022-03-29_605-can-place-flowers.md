---
title: 605. Can Place Flowers
createdAt: 2022-03-28T22:42:25Z
tags: leetcode, algorithm, array
---

# 605. Can Place Flowers

**Question Link**: https://leetcode.com/problems/can-place-flowers/

**Difficulty**: Easy

```swift
/// **Primary idea**: Greedy algorithm. Place flowers as early as possible.
/// **Time Complexity**: O(n) 
/// **Space Complexity**: O(1)
class Solution {
    func canPlaceFlowers(_ flowerbed: [Int], _ n: Int) -> Bool {
        var maxFlowersCouldPlant = 0, flowerbed = flowerbed
        
        for i in 0 ..< flowerbed.count {
            // Check if current flowerbed position can be used to plant a flower
            // otherwise continue to the next position
            guard flowerbed[i] == 0 else {
                continue
            }
            
            // Greedy algorithm. Place flowers as early as possible.
            if i<1 {
                if flowerbed.count == 1 || flowerbed[i+1] == 0 {
                    flowerbed[i] = 1
                    maxFlowersCouldPlant += 1
                }
            } else if i+1 == flowerbed.count {
                if flowerbed.count == 1 || flowerbed[i-1] == 0 {
                    flowerbed[i] = 1
                    maxFlowersCouldPlant += 1
                }
            } else {
                if flowerbed[i-1] == 0 && flowerbed[i+1] == 0 {
                    flowerbed[i] = 1
                    maxFlowersCouldPlant += 1
                }
            }
            
            // Early exit
            if maxFlowersCouldPlant >= n {
                return true
            }
        }
        
        return maxFlowersCouldPlant >= n
    }
}

let solution = Solution()
solution.canPlaceFlowers([1,0,0,0,1], 1)
solution.canPlaceFlowers([1,0,0,0,1], 2)
```