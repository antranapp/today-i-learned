---
title: 206. Reverse Linked List
createdAt: 2022-03-15T23:34:05Z
tags: leetcode, algorithm, linked-list
---

# 206. Reverse Linked List

**Problem**: [206. Reverse Linked List](https://leetcode.com/problems/reverse-linked-list/)

**Difficulty**: Easy

**Primary idea**: Use two helper nodes, traverse the linkedlist and change point direction each time

**Time Complexity**: O(n)

**Space Complexity**: O(1)

```swift
class Solution {
    func reverseList(_ head: ListNode?) -> ListNode? {
        guard let head = head, let next = head.next else {
            return head
        }
        
        let node = reverseList(next)
        next.next = head
        head.next = nil
        
        return node
    }
    
    /// Iterate over the list, reverse the nodes and return the new head node.
    private func reverseList(head: ListNode?) -> ListNode? {
       
        var tempNode: ListNode?
        var firstNode = head
        
        while firstNode != nil {
            // Save the next node
            let secondNode = firstNode!.next
            
            // Reverse the firstNode
            firstNode!.next = tempNode
            
            // Move tempNode ahead
            tempNode = firstNode
            
            // Move firstNode ahead
            firstNode = secondNode
        }
        
        return tempNode
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
let head = ListNode([1,2])
print(head.description)
let reversedHead = solution.reverseList(head)
print(reversedHead!.description)

let head2 = ListNode([1,2,4,5])
print(head2.description)
let reversedHead2 = solution.reverseList(head2)
print(reversedHead2!.description)
```