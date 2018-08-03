# [Remove Nth Node From End of List][title]

## Description

Given a linked list, remove the *n*-th node from the end of list and return its head.

**Example:**

```
Given linked list: 1->2->3->4->5, and n = 2.

After removing the second node from the end, the linked list becomes 1->2->3->5.
```

**Note:**

Given *n* will always be valid.

**Follow up:**

Could you do this in one pass?

**Tags:** Linked List, Two Pointers


## 思路

题意是让你删除链表中的倒数第 n 个数，我的解法是利用双指针，这两个指针相差 n 个元素，<br />
当后面的指针扫到链表末尾的时候，自然它前面的那个指针所指向的下一个元素就是要删除的元素，<br />
即 `pre.next = pre.next.next;`，但是如果一开始后面的指针指向的为空，此时代表的意思就是要删除第一个元素，即 `head = head.next;`。<br />
XCode 编译正确，但是LeetCode现实 compile error，有解决方案的请告诉我。谢谢！！zgpeace@gmail.com

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
    func removeNthFromEnd(_ head: ListNode?, _ n: Int) -> ListNode? {
        var previousNode: ListNode? = head
        var afterNode: ListNode? = head
        var nVar: Int = n

        while nVar != 0 && afterNode != nil {
            nVar -= 1
            afterNode = afterNode!.next
        }
        if afterNode != nil {
            while afterNode!.next != nil {
                afterNode = afterNode!.next
                previousNode = previousNode!.next
            }
            previousNode!.next = previousNode!.next!.next
        } else {
            return head?.next
        }

        return head
    }
}
```


## 结语

如果你同我一样热爱数据结构、算法、LeetCode，可以关注我 GitHub 上的 LeetCode 题解：[awesome-swift-leetcode][zgpeace]



[title]: https://leetcode.com/problems/remove-nth-node-from-end-of-list
[zgpeace]: https://github.com/zgpeace/awesome-swift-leetcode
