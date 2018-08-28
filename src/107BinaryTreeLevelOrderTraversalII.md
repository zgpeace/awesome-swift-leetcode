# [Binary Tree Level Order Traversal II][title]

## Description

Given a binary tree, return the *bottom-up level order* traversal of its nodes' values. (ie, from left to right, level by level from leaf to root).

For example:

Given binary tree `[3,9,20,null,null,15,7]`,

```
    3
   / \
  9  20
    /  \
   15   7
```

return its bottom-up level order traversal as:

```
[
  [15,7],
  [9,20],
  [3]
]
```

**Tags:** Tree, Breadth-first Search


## 思路 0

题意是从下往上按层遍历二叉树，每一层是从左到右，按层遍历，很明显，宽搜第一时间符合，因为是从下往上，所以插入的时候每次插到链表头即可。

```swift
//Definition for a binary tree node.
public class TreeNode {
    public var val: Int
    public var left: TreeNode?
    public var right: TreeNode?
    public init(_ val: Int) {
        self.val = val
        self.left = nil
        self.right = nil
    }
}
 
func levelOrderBottom(_ root: TreeNode?) -> [[Int]] {
    var list: [[Int]] = [[Int]]()
    if root == nil {
        return list
    }
    var queue: [TreeNode] = [TreeNode]()
    queue.append(root!)
    while !queue.isEmpty {
        var subList: [Int] = [Int]()
        let size = queue.count
        for _ in 0..<size {
            let node = queue.removeFirst()
            subList.append(node.val)
            if let leftNode = node.left {
                queue.append(leftNode)
            }
            if let rightNode = node.right {
                queue.append(rightNode)
            }
        }
        list.insert(subList, at: 0)
    }
    
    return list
}
 
```

## 思路 1

另一种思路就是深搜，深搜的时候同时记录深度，然后在相应的层插入节点值即可。

```swift
//Definition for a binary tree node.
public class TreeNode {
    public var val: Int
    public var left: TreeNode?
    public var right: TreeNode?
    public init(_ val: Int) {
        self.val = val
        self.left = nil
        self.right = nil
    }
}

func levelOrderBottomWithDeepestFirst(_ root: TreeNode?) -> [[Int]] {
    var list: [[Int]] = [[Int]]()
    helperWithDeepestFirst(&list, root, 0)
    
    return list
}

func helperWithDeepestFirst(_ list: inout [[Int]], _ root: TreeNode?, _ level: Int) {
    if root == nil {
        return
    }
    if level >= list.count {
        list.insert([Int](), at: 0)
    }
    helperWithDeepestFirst(&list, root?.left, level + 1)
    helperWithDeepestFirst(&list, root?.right, level + 1)
    list[list.count - level - 1].append((root?.val)!)
}

```


## 结语

如果你同我一样热爱数据结构、算法、LeetCode，可以关注我 GitHub 上的 LeetCode 题解：[awesome-swift-leetcode][zgpeace]



[title]: https://leetcode.com/problems/binary-tree-level-order-traversal-ii
[zgpeace]: https://github.com/zgpeace/awesome-swift-leetcode
