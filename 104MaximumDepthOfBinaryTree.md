# [Maximum Depth of Binary Tree][title]

## Description

Given a binary tree, find its maximum depth.

The maximum depth is the number of nodes along the longest path from the root node down to the farthest leaf node.

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

return its depth = 3.

**Tags:** Tree, Depth-first Search


## 思路

题意是找到二叉树的最大深度，很明显，深搜即可，每深入一次节点加一即可，然后取左右子树的最大深度。

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

func maxDepth(_ root: TreeNode?) -> Int {
    if root == nil {
        return 0;
    }
    return 1 + max(maxDepth(root?.left), maxDepth(root?.right))
}
```


## 结语

如果你同我一样热爱数据结构、算法、LeetCode，可以关注我 GitHub 上的 LeetCode 题解：[awesome-swift-leetcode][zgpeace]



[title]: https://leetcode.com/problems/maximum-depth-of-binary-tree
[zgpeace]: https://github.com/zgpeace/awesome-swift-leetcode
