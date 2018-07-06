# [Remove Duplicates from Sorted List][title]

## Description

Given a sorted linked list, delete all duplicates such that each element appear only *once*.

**Example 1:**

```
Input: 1->1->2
Output: 1->2
```

**Example 2:**

```
Input: 1->1->2->3->3
Output: 1->2->3
```

**Tags:** Linked List


## 思路

题意是删除链表中重复的元素，很简单，我们只需要遍历一遍链表，遇到链表中相邻元素相同时，把当前指针指向下下个元素即可。

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

func buildNodeList(arrayParam: [Int]) -> ListNode {
    let head = ListNode(0)
    var listNode = head
    for item in arrayParam {
        listNode.next = ListNode(item)
        listNode = listNode.next!
    }
    
    return head.next!
}

func deleteDuplicates(_ head: ListNode?) -> ListNode? {
    if head == nil || head?.next == nil {
        return head
    }
    var current = head
    while current?.next != nil {
        if current?.val == current?.next?.val {
            current?.next = current?.next?.next
        } else {
            current = current?.next
        }
    }
    
    return head
}

let input1 = [1, 1, 2]
let listNode1 = buildNodeList(arrayParam: input1)
print("input: \(listNode1.nodeString()); output: \(String(describing: deleteDuplicates(listNode1)?.nodeString()))")

let input2 = [1, 1, 2, 3, 3]
let listNode2 = buildNodeList(arrayParam: input2)
print("input: \(listNode2.nodeString()); output: \(String(describing: deleteDuplicates(listNode2)?.nodeString()))")

```


## 结语

如果你同我一样热爱数据结构、算法、LeetCode，可以关注我 GitHub 上的 LeetCode 题解：[awesome-swift-leetcode][zgpeace]



[title]: https://leetcode.com/problems/remove-duplicates-from-sorted-list
[zgpeace]: https://github.com/zgpeace/awesome-swift-leetcode
