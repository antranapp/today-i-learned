---
title: 2. Add Two Numbers
createdAt: 2022-03-17T22:35:28Z
tags: leetcode, algorithm, linked-list
---

# 2. Add Two Numbers

**Question Link**: https://leetcode.com/problems/add-two-numbers/

**Diificulty**: Medium

**Primary idea**: use carry and iterate through both linked lists

**Time Complexity**: O(n), Space Complexity: O(1)


```swift
class Solution {
    func addTwoNumbers(_ l1: ListNode?, _ l2: ListNode?) -> ListNode? {
        var carry: Int = 0
        var firstNode = l1
        var secondNode = l2
        let savedHeadOutputNode: ListNode? = ListNode(-1)
        var outputNode = savedHeadOutputNode
        
        while firstNode != nil || secondNode != nil {
            var sum = carry
            if firstNode != nil {
                sum += firstNode!.val
                firstNode = firstNode?.next
            }
            
            if secondNode != nil {
                sum += secondNode!.val
                secondNode = secondNode?.next
            }
            outputNode?.next = ListNode(sum % 10)
            outputNode = outputNode?.next
            carry = sum / 10
        }
        
        if carry > 0 {
            outputNode?.next = ListNode(carry)
        }
        
        return savedHeadOutputNode?.next
    }
    
    func addTwoNumbersRecursive(l1: ListNode?, _ l2: ListNode?) -> ListNode? {
        guard let l1 = l1 else {return l2}
        guard let l2 = l2 else {return l1}
        
        let outputNode = ListNode((l1.val + l2.val)%10)
        if l1.val + l2.val > 9 {
            outputNode.next = addTwoNumbers(addTwoNumbers(l1.next, l2.next),
                                            ListNode(1))
        } else {
            outputNode.next = addTwoNumbers(l1.next, l2.next)
        }
        
        
        return outputNode
    }
}

class ListNode {
    var val: Int
    var next: ListNode?
    
    init(_ vals: [Int]) {
        self.val = vals[0]
        var first: ListNode? = self
        for i in 1..<vals.count {
            first?.next = ListNode(vals[i])
            first = first?.next
        }
    }
    init() { self.val = 0; self.next = nil; }
    init(_ val: Int) { self.val = val; self.next = nil; }
    init(_ val: Int, _ next: ListNode?) { self.val = val; self.next = next; }
    
    var description: String {
        var result = [String]()
        var firstNode: ListNode? = self
        while firstNode != nil {
            result.append("\(firstNode!.val)")
            firstNode = firstNode?.next
        }
        
        return result.joined(separator: ",")
    }
}

let solution = Solution()
let first = ListNode([2,4,3])
print(first.description)
let second = ListNode([5,6,4])
print(second.description)
let result = solution.addTwoNumbers(first, second)
print(result?.description)

let first2 = ListNode([9,9,9,9,9,9,9])
print(first2.description)
let second2 = ListNode([9,9,9])
print(second2.description)
let result2 = solution.addTwoNumbers(first2, second2)
print(result2?.description)
```