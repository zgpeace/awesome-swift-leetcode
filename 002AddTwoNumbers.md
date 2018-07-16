# [Add Two Numbers][title]

## Description

You are given two **non-empty** linked lists representing two non-negative integers. The digits are stored in **reverse order** and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

**Example**

```
Input: (2 -> 4 -> 3) + (5 -> 6 -> 4)
Output: 7 -> 0 -> 8
Explanation: 342 + 465 = 807.
```

**Tags:** Linked List, Math


## 思路

题意是以链表表示一个数，低位在前，高位在后，所以题中的例子就是 `342 + 465 = 807`，所以我们模拟计算即可。

```swift
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     public var val: Int
 *     public var next: ListNode?
 *     public init(_ val: Int) {
 *         self.val = val
 *         self.next = nil
 *     }
 * }
 */
class Solution {
    func addTwoNumbers(_ l1: ListNode?, _ l2: ListNode?) -> ListNode? {
        var resultNode:ListNode = ListNode(0)
        let headNode = resultNode
        var node1 = l1
        var node2 = l2
        var sum:Int = 0

        while node1 != nil || node2 != nil {
            sum = sum / 10
            if node1 != nil {
                sum += (node1?.val)!
                node1 = node1?.next
            }
            if node2 != nil {
                sum += (node2?.val)!
                node2 = node2?.next
            }
            resultNode.next = ListNode(sum % 10)
            resultNode = resultNode.next!
        }
        if sum / 10 != 0 {
            resultNode.next = ListNode(1)
        }

        return headNode.next
    }
}
```


## 结语

如果你同我一样热爱数据结构、算法、LeetCode，可以关注我 GitHub 上的 LeetCode 题解：[awesome-swift-leetcode][zgpeace]



[title]: https://leetcode.com/problems/add-two-numbers
[zgpeace]: https://github.com/zgpeace/awesome-swift-leetcode
