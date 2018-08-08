# [Swap Nodes in Pairs][title]

## Description

Given a linked list, swap every two adjacent nodes and return its head.

**Example:**

```
Given 1->2->3->4, you should return the list as 2->1->4->3.
```

**Note:**

- Your algorithm should use only constant extra space.
- You may **not** modify the values in the list's nodes, only nodes itself may be changed.

**Tags:** Linked List


## 思路 0

题意是让你交换链表中相邻的两个节点，最终返回交换后链表的头，限定你空间复杂度为 O(1)。我们可以用递归来算出子集合的结果，递归的终点就是指针指到链表末少于两个元素时，如果不是终点，那么我们就对其两节点进行交换，这里我们需要一个临时节点来作为交换桥梁，就不多说了。

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
    func swapPairs(_ head: ListNode?) -> ListNode? {
        //method 0: recursive
        if head == nil || head?.next == nil {
            return head
        }
        let temp = head!.next
        head!.next = swapPairs(temp!.next)
        temp!.next = head

        return temp
    }
}
```


## 思路 1

另一种实现方式就是用循环来实现了，两两交换节点，也需要一个临时节点来作为交换桥梁，直到当前指针指到链表末少于两个元素时停止，代码很简单，如下所示。

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
    func swapPairs(_ head: ListNode?) -> ListNode? {
        let preHead: ListNode? = ListNode(0)
        var current: ListNode? = preHead
        current!.next = head
        while current!.next != nil && current!.next?.next != nil  {
            let temp: ListNode = current!.next!.next!
            current!.next!.next = temp.next
            temp.next = current?.next
            current!.next = temp
            current = temp.next
        }

        return preHead?.next
    }
}
```


## 结语

如果你同我一样热爱数据结构、算法、LeetCode，可以关注我 GitHub 上的 LeetCode 题解：[awesome-swift-leetcode][zgpeace]



[title]: https://leetcode.com/problems/swap-nodes-in-pairs
[zgpeace]: https://github.com/zgpeace/awesome-swift-leetcode
