---
title: 169. Majority Element
createdAt: 2022-03-21T22:18:54Z
tags: leetcode, algorithm, array
---

# 169. Majority Element

 **Question Link**: https://leetcode.com/problems/majority-element/

 **Difficulty**: Easy
 
 **Primary idea**: 
    - **Method 1**: Boyer-Moore voting algorithm: traverse the array and track the majority element accordingly
    - **Method 2**: Hashtable: In Hashmap(key-value pair), at value, maintain a count for each element(key) and whenever the count is greater than half of the array length, return that key(majority element). 
 
 **Time Complexity**: O(n) 
 
 **Space Complexity**: 
    - **Method 1**: O(1) 
    - **Method 2**: O(n)

 **Further Info**: https://www.geeksforgeeks.org/majority-element/

```swift
class Solution {
    // Boyer-Moore voting algorithm
    // This algorithm only works when there is a guaranteed a majority candidate
    func majorityElement(_ nums: [Int]) -> Int {
        var count = 0, majorityCandidate = 0
        
        for num in nums {
            if count == 0 {
                majorityCandidate = num
            }
            
            count += (majorityCandidate == num) ? 1 : -1
        }
        
        return majorityCandidate
    }
    
    // In Hashmap(key-value pair), at value, maintain a count for each element(key) and whenever the count is greater than half of the array length, return that key(majority element). 
    // This algorithm return -1 when there is no majority element
    func majorityElementHashtable(_ nums: [Int]) -> Int {
        var occurences = [Int: Int]()
        for num in nums {
            if let occurence = occurences[num] {
                let newOccurence = occurence + 1
                if newOccurence > nums.count / 2 {
                    return num
                } else {
                    occurences[num] = newOccurence
                }
            } else {
                occurences[num] = 1
            }
        }
        
        return -1
    }
}

let solution = Solution()
solution.majorityElement([3,2,3])
solution.majorityElement([2,2,1,1,1,2,2])
solution.majorityElement([3,3,4,2,4,4,2,4,4])
solution.majorityElement([1,1,2,2])
solution.majorityElementHashtable([1,3,3,1,2])
solution.majorityElementHashtable([1,3,3,1,2,3])
solution.majorityElementHashtable([1,3,3,1,2,3,3])
```