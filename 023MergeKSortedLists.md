# [Merge k Sorted Lists][title]

## Description

Merge *k* sorted linked lists and return it as one sorted list. Analyze and describe its complexity.

**Example:**

```
Input:
[
  1->4->5,
  1->3->4,
  2->6
]
Output: 1->1->2->3->4->4->5->6
```

**Tags:** Linked List, Divide and Conquer, Heap


## 思路 0

题意是合并多个已排序的链表，分析并描述其复杂度，我们可以用分治法来两两合并他们，假设 `k` 为总链表个数，`N` 为总元素个数，那么其时间复杂度为 `O(Nlogk)`。

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
    func mergeKLists(_ lists: [ListNode?]) -> ListNode? {
      if lists.count == 0 {
            return nil
        }

        return helper(lists, 0, lists.count - 1)
    }

    func helper(_ lists: [ListNode?], _ left: Int, _ right: Int) -> ListNode? {
        if left >= right {
            return lists[left]
        }
        let mid: Int = (left + right) >> 1
        let l0: ListNode? = helper(lists, left, mid)
        let l1: ListNode? = helper(lists, mid + 1, right)

        return merge2ListNode(l0, l1)
    }

    func merge2ListNode(_ nodeFirst: ListNode?, _ nodeSecond: ListNode?) -> ListNode? {
        var nodeFirst = nodeFirst
        var nodeSecond = nodeSecond
        let node: ListNode = ListNode(0)
        var temp: ListNode = node
        while nodeFirst != nil && nodeSecond != nil {
            if nodeFirst!.val < nodeSecond!.val {
                temp.next = ListNode(nodeFirst!.val)
                nodeFirst = nodeFirst!.next
            } else {
                temp.next = ListNode(nodeSecond!.val)
                nodeSecond = nodeSecond!.next
            }

            temp = temp.next!
        }

        temp.next = nodeFirst != nil ? nodeFirst : nodeSecond

        return node.next
    }
}
```


## 结语

如果你同我一样热爱数据结构、算法、LeetCode，可以关注我 GitHub 上的 LeetCode 题解：[awesome-swift-leetcode][zgpeace]



[title]: https://leetcode.com/problems/merge-k-sorted-lists
[zgpeace]: https://github.com/zgpeace/awesome-swift-leetcode
