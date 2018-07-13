# [Diameter of Binary Tree][title]

## Description

Given a binary tree, you need to compute the length of the diameter of the tree. The diameter of a binary tree is the length of the **longest** path between any two nodes in a tree. This path may or may not pass through the root.

**Example:**
Given a binary tree 

```
          1
         / \
        2   3
       / \     
      4   5    
```

Return **3**, which is the length of the path [4,2,1,3] or [5,2,1,3].

**Note:** The length of path between two nodes is represented by the number of edges between them.

**Tags:** Tree


## 思路

题意是让你算出二叉树中最远的两个节点的距离，分别计算左右子树的最大高度，然后不断迭代出其和的最大值就是最终结果。

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
    var max = 0
    func diameterOfBinaryTree(_ root: TreeNode?) -> Int {
        helper(root)
        return max
    }

    func helper(_ node: TreeNode?) -> Int {
        if node == nil {
            return 0
        }
        let leftInt: Int = helper(node?.left)
        let rightInt: Int = helper(node?.right)
        let distance = leftInt + rightInt
        if distance > max {
            max = distance
        }
        return 1 + Swift.max(leftInt, rightInt)
    }
}
```


## 结语

如果你同我一样热爱数据结构、算法、LeetCode，可以关注我 GitHub 上的 LeetCode 题解：[awesome-swift-leetcode][zgpeace]



[title]: https://leetcode.com/problems/diameter-of-binary-tree
[zgpeace]: https://github.com/zgpeace/awesome-swift-leetcode
