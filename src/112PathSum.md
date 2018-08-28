# [Path Sum][title]

## Description

Given a binary tree and a sum, determine if the tree has a root-to-leaf path such that adding up all the values along the path equals the given sum.

**Note:** A leaf is a node with no children.

**Example:**

Given the below binary tree and `sum = 22`,

```
      5
     / \
    4   8
   /   / \
  11  13  4
 /  \      \
7    2      1
```

return true, as there exist a root-to-leaf path `5->4->11->2` which sum is 22.

**Tags:** Tree, Depth-first Search


## 思路

题意是查找二叉树中是否存在从根结点到叶子的路径和为某一值，利用深搜在遇到叶子节点时判断是否满足即可。


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
    func hasPathSum(_ root: TreeNode?, _ sum: Int) -> Bool {
        if root == nil {
            return false
        }
        if root?.left == nil && root?.right == nil {
            return sum == root?.val
        }
        let sumLess: Int = sum - (root?.val)!

        return hasPathSum(root?.left, sumLess) || hasPathSum(root?.right, sumLess)
        }
}
```


## 结语

如果你同我一样热爱数据结构、算法、LeetCode，可以关注我 GitHub 上的 LeetCode 题解：[awesome-swift-leetcode][zgpeace]



[title]: https://leetcode.com/problems/path-sum
[zgpeace]: https://github.com/zgpeace/awesome-swift-leetcode
