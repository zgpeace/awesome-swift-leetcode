# [Pascal's Triangle II][title]

## Description

Given a non-negative index *k* where *k* ≤ 33, return the *k*th index row of the Pascal's triangle.

Note that the row index starts from 0.

![img](https://upload.wikimedia.org/wikipedia/commons/0/0d/PascalTriangleAnimated2.gif)
In Pascal's triangle, each number is the sum of the two numbers directly above it.

**Example:**

```
Input: 3
Output: [1,3,3,1]
```

**Follow up:**

Could you optimize your algorithm to use only *O*(*k*) extra space?

**Tags:** Array


## 思路

 题意是指定输出帕斯卡尔三角形的某一行，模拟即可，<br />
 观察规律：<br />
 1、每行的个数为rowIndex + 1, 比如 rowIndex = 0, num = 1<br />
 2、下一行比上一行多一个数，比如 f(n + 1) - f(n) = 1<br />
 3、每行的首尾都是1，所以只要计算1 ~ Max - 1。<br />
 4、O(k)的空间只能用一维数组，为了不污染前面的数据，所以送从后面算起即可<br />
 优化后的代码如下所示。<br />

```swift
class Solution {
    func getRow(_ rowIndex: Int) -> [Int] {
        var list: [Int] = [Int]()
        for i in 0...rowIndex {
            list.append(1)
            var j = i - 1
            while j > 0 {
                list[j] = list[j - 1] + list[j]
                j -= 1
            }
        }

        return list
    }
}
```


## 结语

如果你同我一样热爱数据结构、算法、LeetCode，可以关注我 GitHub 上的 LeetCode 题解：[awesome-swift-leetcode][zgpeace]



[title]: https://leetcode.com/problems/pascals-triangle-ii
[zgpeace]: https://github.com/zgpeace/awesome-swift-leetcode
