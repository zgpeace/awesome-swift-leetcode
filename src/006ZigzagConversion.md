# [ZigZag Conversion][title]

## Description

The string `"PAYPALISHIRING"` is written in a zigzag pattern on a given number of rows like this: (you may want to display this pattern in a fixed font for better legibility)

```
P   A   H   N
A P L S I I G
Y   I   R
```

And then read line by line: `"PAHNAPLSIIGYIR"`

Write the code that will take a string and make this conversion given a number of rows:

```
string convert(string s, int numRows);
```

**Example 1:**

```
Input: s = "PAYPALISHIRING", numRows = 3
Output: "PAHNAPLSIIGYIR"
```

**Example 2:**

```
Input: s = "PAYPALISHIRING", numRows = 4
Output: "PINALSIGYAHRPI"
Explanation:

P     I    N
A   L S  I G
Y A   H R
P     I
```

**Tags:** String


## 思路 0

题意是让你把字符串按波浪形排好，然后返回横向读取的字符串。

听不懂的话，看下面的表示应该就明白了：

```
0                           2n-2                        4n-4
1                    2n-3   2n-1                 4n-5   4n-5
2              2n-4         2n               4n-6       .
.           .               .             .             .
.       n+1                 .          3n-1             .
n-2   n                     3n-4   3n-2                 5n-6
n-1                         3n-3                        5n-5
```

那么我们可以根据上面找规律，可以看到波峰和波谷是单顶点的，它们周期是 `2 * (n - 1)`，单独处理即可；中间的部分每个周期会出现两次，规律很好找，留给读者自己想象，不懂的可以结合以下代码。

```swift
func convert(_ s: String, _ numRows: Int) -> String {
    if numRows <= 1 {
        return s
    }
    var result: String = ""
    let len = s.count
    let cycle = 2 * (numRows - 1)
    
    //first row
    var i = 0
    while i < len {
        result.append(s[s.index(s.startIndex, offsetBy: i)])
        i += cycle
    }
    
    //middle rows
    for j in 1..<(numRows-1) {
        var step = j * 2
        var varJ = j
        while varJ < len {
            result.append(s[s.index(s.startIndex, offsetBy: varJ)])
            step = cycle - step
            varJ += step
        }
        
    }
    
    //last row
    var k = numRows - 1
    while k < len {
        result.append(s[s.index(s.startIndex, offsetBy: k)])
        k += cycle
    }
    
    return result
}
```


## 思路 1

另外一种思路就是开辟相应行数的 `StringBuilder` 对象，然后模拟波浪生成的样子分别插入到相应的 `StringBuilder` 对象，比较直白简单，具体代码如下。

```swift
func convertWithRowSubString(_ s: String, _ numRows: Int) -> String {
    if numRows <= 1 {
        return s
    }
    let len = s.count
//    let cycle = 2 * (numRows - 1)
    
    var rowArray: [String] = [String](repeating: "", count: numRows)
    var i = 0
    while i < len {
        //垂直方向
        var k = 0
        while k < numRows && i < len {
            rowArray[k].append(s[s.index(s.startIndex, offsetBy: i)])
            i += 1
            k += 1
        }
        
        k = numRows - 2
        //倾斜方向
        while k >= 1 && i < len {
            rowArray[k].append(s[s.index(s.startIndex, offsetBy: i)])
            i += 1
            k -= 1
        }
    }
    
    for item in 1..<numRows {
        rowArray[0] += rowArray[item]
    }
    
    return rowArray[0]
}
```


## 结语

如果你同我一样热爱数据结构、算法、LeetCode，可以关注我 GitHub 上的 LeetCode 题解：[awesome-swift-leetcode][zgpeace]



[title]: https://leetcode.com/problems/zigzag-conversion
[zgpeace]: https://github.com/zgpeace/awesome-swift-leetcode
