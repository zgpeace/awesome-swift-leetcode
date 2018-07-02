# [Merge Two Sorted Lists][title]

## Description

Merge two sorted linked lists and return it as a new list. The new list should be made by splicing together the nodes of the first two lists.

**Example:**

```
Input: 1->2->4, 1->3->4
Output: 1->1->2->3->4->4
```

**Tags:** Linked List


## 思路

题意是用一个新链表来合并两个已排序的链表，那我们只需要从头开始比较已排序的两个链表，新链表指针每次指向值小的节点，依次比较下去，最后，当其中一个链表到达了末尾，我们只需要把新链表指针指向另一个没有到末尾的链表此时的指针即可。

```swift
public class ListNode {
    public var val: Int
    public var next: ListNode?
    public init(_ val: Int) {
        self.val = val
        self.next = nil
    }
    
    func nodeString() -> String {
        var description = ""
        var temp = self
        while temp != nil {
            description += "\(temp.val) "
            if let tempNext = temp.next {
                temp = tempNext
            } else {
                return description
            }
        }
        
        return description
    }
}

func mergeTwoLists(_ l1: ListNode?, _ l2: ListNode?) -> ListNode? {
    let head:ListNode = ListNode(0)
    var result:ListNode = head
    var l1 = l1
    var l2 = l2
    
    while l1 != nil && l2 != nil {
        if (l1?.val)! < (l2?.val)! {
            result.next = l1
            l1 = l1?.next
        } else {
            result.next = l2
            l2 = l2?.next
        }
        result = result.next!
    }
    
    result.next = (l1 != nil) ? l1 : l2
    
    return head.next
}

func buildNodeList(arrayParam: [Int]) -> ListNode {
    let head = ListNode(0)
    var listNode = head
    for item in arrayParam {
        listNode.next = ListNode(item)
        listNode = listNode.next!
    }
    
    return head.next!
}

var array1:[Int] = [1, 2, 4]
var array2:[Int] = [1, 3, 4]
var l1 = buildNodeList(arrayParam: array1)
var l2 = buildNodeList(arrayParam: array2)

print("l1: \(l1.nodeString())")
print("l2: \(l2.nodeString())")

var result = mergeTwoLists(l1, l2)
print("result: \(String(describing: result?.nodeString()))")
```


## 结语

如果你同我一样热爱数据结构、算法、LeetCode，可以关注我 GitHub 上的 LeetCode 题解：[awesome-swift-leetcode][zgpeace]



[title]: https://leetcode.com/problems/merge-two-sorted-lists
[zgpeace]: https://github.com/zgpeace/awesome-swift-leetcode
