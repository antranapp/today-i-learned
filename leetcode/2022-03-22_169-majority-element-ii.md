---
title: 229. Majority Element II
createdAt: 2022-03-21T22:30:08Z
tags: leetcode, algorithm, array
---

# 169. Majority Element II

**Question Link**: https://leetcode.com/problems/majority-element/

 **Difficulty**: Medium
 
 **Primary idea**: 
    - **Method 1**: Use modified Boyer-Moore algorithm. There are at most two majority elements, and the number of non-majority elements must be fewer than either of them. Thus, we can maintain two counters. If a number equals to one of the candidates, the corresponding counter +1 while the other does not change; if a number does not equal to either of them, both counters -1. If a counter is 0, replace the candidate with the next number. At the end, verify both of them occurred more than ⌊ n/3 ⌋ times, because some times there is only one majority element.
    - **Method 2**: Hashtable: In Hashmap(key-value pair), at value, maintain a count for each element(key) and whenever the count is greater than half of the array length, return that key(majority element). 
 
 **Time Complexity**: O(n) 
 
 **Space Complexity**: 
    - **Method 1**: O(1) 
    - **Method 2**: O(n)

```swift
class Solution {
    func majorityElement(_ nums: [Int]) -> [Int] {
        var num0: Int?
        var num1: Int?
        var count0 = 0
        var count1 = 0
        var res = [Int]()
        
        for num in nums {
            if let num0 = num0, num0 == num {
                count0 += 1
            } else if let num1 = num1, num1 == num {
                count1 += 1
            } else if count0 == 0 {
                num0 = num
                count0 = 1
            } else if count1 == 0 {
                num1 = num
                count1 = 1
            } else {
                count0 -= 1
                count1 -= 1
            }
        }
        
        count0 = 0
        count1 = 0
        
        for num in nums {
            if num == num0 {
                count0 += 1
            }
            if num == num1 {
                count1 += 1
            }
        }
        
        if count0 > nums.count / 3 {
            res.append(num0!)
        }
        if count1 > nums.count / 3 {
            res.append(num1!)
        }
        
        return res
    }

    func majorityElementHashtable(_ nums: [Int]) -> [Int] {
        var occurences = [Int: Int]()
        var result = [Int]()
        for num in nums {
            if let occurence = occurences[num] {
                occurences[num] = occurence + 1
            } else {
                occurences[num] = 1
            }
        }
        
        for (_, element) in occurences.enumerated() {
            if element.value > nums.count / 3 {
                result.append(element.key)
            }
        }
        
        return result
    }
}

let solution = Solution()
solution.majorityElement([3,2,3])
solution.majorityElement([2,2,1,1,1,2,2])
solution.majorityElement([3,3,4,2,4,4,2,4,4])
solution.majorityElement([1,1,2,2])
```