# [Balanced Binary Tree][title]

## Description

Given a binary tree, determine if it is height-balanced.

For this problem, a height-balanced binary tree is defined as:

> a binary tree in which the depth of the two subtrees of *every* node never differ by more than 1.

**Example 1:**

Given the following tree `[3,9,20,null,null,15,7]`:

```
    3
   / \
  9  20
    /  \
   15   7
```

Return true.
**Example 2:**

Given the following tree `[1,2,2,3,3,null,null,4,4]`:

```
       1
      / \
     2   2
    / \
   3   3
  / \
 4   4
```

Return false.

**Tags:** Tree, Depth-first Search


## 思路

题意是判断一棵二叉树是否是高度平衡的，所谓二叉树高度平衡指的是二叉树的每个节点的两棵子树的高度差都不超过 1，那么我们只需计算左右子树的高度，判断其高度差是否不超过 1 即可，如果超过 1，就代表其不是高度平衡的，立即返回不是即可，我这里用返回 `-1` 代表不是。

```swift
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     public var val: Int
 *     public var left: TreeNode?
 *     public var right: TreeNode?
 *     public init(_ val: Int) {
 *         self.val = val
 *         self.left = nil
 *         self.right = nil
 *     }
 * }
 */
class Solution {
    func isBalanced(_ root: TreeNode?) -> Bool {
    return helper(root) != -1
}

func helper(_ node: TreeNode?) -> Int {
    guard let node = node else {
        return 0
    }
    let leftInt = helper(node.left)
    if leftInt == -1 {
        return -1
    }
    let rightInt = helper(node.right)
    if rightInt == -1 {
        return -1
    }
    if abs(leftInt - rightInt) > 1 {
        return -1
    }
    return 1 + max(leftInt, rightInt)
}
}
```


## 结语

如果你同我一样热爱数据结构、算法、LeetCode，可以关注我 GitHub 上的 LeetCode 题解：[awesome-swift-leetcode][zgpeace]



[title]: https://leetcode.com/problems/balanced-binary-tree
[zgpeace]: https://github.com/zgpeace/awesome-swift-leetcode
