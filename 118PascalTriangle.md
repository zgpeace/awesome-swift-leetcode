# [Pascal's Triangle][title]

## Description

Given a non-negative integer *numRows*, generate the first *numRows* of Pascal's triangle.

![img](https://upload.wikimedia.org/wikipedia/commons/0/0d/PascalTriangleAnimated2.gif)
In Pascal's triangle, each number is the sum of the two numbers directly above it.

**Example:**

```
Input: 5
Output:
[
     [1],
    [1,1],
   [1,2,1],
  [1,3,3,1],
 [1,4,6,4,1]
]
```

**Tags:** Array


## 思路

题意是给出行数，输出帕斯卡尔三角形，很简单的模拟，就不多说了。

```swift
class Solution {
    func generate(_ numRows: Int) -> [[Int]] {
        var list = [[Int]]()
    
        if numRows < 1 {
            return list
        }
        for i in 0..<numRows {
            var subList = [Int]()
            for j in 0...i {
                if j == 0 || j == i {
                    subList.append(1)
                    continue
                }

                let preList = list[i - 1]
                subList.append(preList[j - 1] + preList[j])
            }

            list.append(subList)
        }

        return list
    }
}
```


## 结语

如果你同我一样热爱数据结构、算法、LeetCode，可以关注我 GitHub 上的 LeetCode 题解：[awesome-swift-leetcode][zgpeace]



[title]: https://leetcode.com/problems/pascals-triangle
[zgpeace]: https://github.com/zgpeace/awesome-swift-leetcode
