# [Minimum Depth of Binary Tree][title]

## Description

Given a binary tree, find its minimum depth.

The minimum depth is the number of nodes along the shortest path from the root node down to the nearest leaf node.

**Note:** A leaf is a node with no children.

**Example:**

Given binary tree `[3,9,20,null,null,15,7]`,

```
    3
   / \
  9  20
    /  \
   15   7
```

return its minimum depth = 2.

**Tags:** Tree, Depth-first Search, Breadth-first Search


## 思路 0

题意是查找二叉树的最小深度，也就是找到从根结点到叶子节点的最小深度，最容易想到的当然是深搜，如果节点的左右深度都不是 0 的话，说明该节点含有左右子树，所以它的最小高度就是 1 加上其左右子树高度较小者，否则如果左子树为空或者右子树为空或者两者都为空，那么就是 1 加上非空子树高度。

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

func minDepth(_ root: TreeNode?) -> Int {
    return helperForDeepFisrt(root)
}

func helperForDeepFisrt(_ node: TreeNode?) -> Int {
    if node == nil {
        return 0
    }
    let leftInt = helperForDeepFisrt(node?.left)
    let rightInt = helperForDeepFisrt(node?.right)
    if leftInt != 0 && rightInt != 0 {
        return 1 + min(leftInt, rightInt)
    }
    return 1 + leftInt + rightInt
}

```

## 思路 1

第二种思路就是利用宽搜了，搜索到该层有叶子节点，那就返回该层宽度即可。

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

func minDepthForBreadthFirst(_ root: TreeNode?) -> Int {
    if root == nil {
        return 0
    }
    var list: [TreeNode] = [TreeNode]()
    list.append(root!)
    var minDepth = 1
    while list.count != 0 {
        let size = list.count
        for _ in 0..<size {
            let node = list.removeFirst()
            if node.left == nil && node.right == nil {
                return minDepth
            }
            if let leftNode = node.left {
                list.append(leftNode)
            }
            if let rightNode = node.right {
                list.append(rightNode)
            }
            
        }
        minDepth += 1
    }
    
    return minDepth
}

```


## 结语

如果你同我一样热爱数据结构、算法、LeetCode，可以关注我 GitHub 上的 LeetCode 题解：[awesome-swift-leetcode][zgpeace]



[title]: https://leetcode.com/problems/minimum-depth-of-binary-tree
[zgpeace]: https://github.com/zgpeace/awesome-swift-leetcode
