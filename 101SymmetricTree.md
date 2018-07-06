# [Symmetric Tree][title]

## Description

Given a binary tree, check whether it is a mirror of itself (ie, symmetric around its center).

For example, this binary tree `[1,2,2,3,4,4,3]` is symmetric:

```
    1
   / \
  2   2
 / \ / \
3  4 4  3
```

But the following `[1,2,2,null,3,null,3]` is not:

```
    1
   / \
  2   2
   \   \
   3    3
```

**Note:**

Bonus points if you could solve it both recursively and iteratively.

**Tags:** Tree, Depth-first Search, Breadth-first Search


## 思路 0

题意是判断一棵二叉树是否左右对称，首先想到的是深搜，比较根结点的左右两棵子树是否对称，如果左右子树的值相同，那么再分别对左子树的左节点和右子树的右节点，左子树的右节点和右子树的左节点做比较即可。

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

func isSymmetric(_ root: TreeNode?) -> Bool {
    return root == nil || isSymmetricHelper(root?.left, root?.right)
}

func isSymmetricHelper(_ leftNode: TreeNode?, _ rightNode: TreeNode?) -> Bool {
    if leftNode == nil && rightNode == nil {
        return true
    }
    if leftNode == nil || rightNode == nil {
        return false
    }
    if leftNode?.val != rightNode?.val {
        return false
    }
    return isSymmetricHelper(leftNode?.left, rightNode?.right) && isSymmetricHelper(leftNode?.right, rightNode?.left)
}

```

## 思路 1

第二种思路就是宽搜了，宽搜肯定要用到队列，Java 中可用 `LinkedList` 替代，也是要做到左子树的左节点和右子树的右节点，左子树的右节点和右子树的左节点做比较即可。
Swift中用数组代替，每次都获取first item, 接着remove掉，保证先进先出FIFO
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

func isSymmetricWithIteratively(_ root: TreeNode?) -> Bool {
    if root == nil {
        return true
    }
    var linkList: [TreeNode] = [TreeNode]();
    if root?.left == nil && root?.right == nil {
        return true
    }
    if root?.left == nil || root?.right == nil {
        return false
    }
    linkList.append((root?.left)!)
    linkList.append((root?.right)!)
    var leftNode: TreeNode? = nil
    var rightNode: TreeNode? = nil
    while linkList.count > 0 {
        leftNode = linkList.first
        linkList.remove(at: 0)
        rightNode = linkList.first
        linkList.remove(at: 0)
        
        if leftNode?.val != rightNode?.val {
            return false
        }
        
        if !(leftNode?.left == nil && rightNode?.right == nil) && (leftNode?.left == nil || rightNode?.right == nil) {
            return false
        } else if(leftNode?.left != nil && rightNode?.right != nil) {
            linkList.append((leftNode?.left)!)
            linkList.append((rightNode?.right)!)
        }
        
        if !(leftNode?.right == nil && rightNode?.left == nil) && (leftNode?.right == nil || rightNode?.left == nil) {
            return false
        } else if(leftNode?.right != nil && rightNode?.left != nil) {
            linkList.append((leftNode?.right)!)
            linkList.append((rightNode?.left)!)
        }
        
    }
    
    return true
}

```


## 结语

如果你同我一样热爱数据结构、算法、LeetCode，可以关注我 GitHub 上的 LeetCode 题解：[awesome-swift-leetcode][zgpeace]



[title]: https://leetcode.com/problems/symmetric-tree
[zgpeace]: https://github.com/zgpeace/awesome-swift-leetcode
