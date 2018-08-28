# [Add Binary][title]

## Description

Given two binary strings, return their sum (also a binary string).

The input strings are both **non-empty** and contains only characters `1` or `0`.

**Example 1:**

```
Input: a = "11", b = "1"
Output: "100"
```

**Example 2:**

```
Input: a = "1010", b = "1011"
Output: "10101"
```

**Tags:** Math, String


## 思路

题意是给你两个二进制串，求其和的二进制串。我们就按照小学算数那么来做，用 `carry` 表示进位，从后往前算，依次往前，每算出一位就插入到最前面即可，直到把两个二进制串都遍历完即可。

```swift
func addBinary(_ a: String, _ b: String) -> String {
    var result = String()
    var aLastIndex = a.count - 1
    var bLastIndex = b.count - 1
    var carray: Int = 0
    
    while aLastIndex >= 0 && bLastIndex >= 0 {
        carray = carray + (aLastIndex >= 0 ? Int(String(a[a.index(a.startIndex, offsetBy: aLastIndex)]))! : 0)
        carray = carray + (bLastIndex >= 0 ? Int(String(b[b.index(b.startIndex, offsetBy: bLastIndex)]))! : 0)
        
        let tempString = String(carray % 2)
        result.insert(tempString[tempString.startIndex], at: result.startIndex)
        carray = carray >> 1
        aLastIndex -= 1
        bLastIndex -= 1
    }
    while aLastIndex >= 0 {
        carray = carray + (aLastIndex >= 0 ? Int(String(a[a.index(a.startIndex, offsetBy: aLastIndex)]))! : 0)
        let tempString = String(carray % 2)
        result.insert(tempString[tempString.startIndex], at: result.startIndex)
        carray = carray >> 1
        aLastIndex -= 1
    }
    while bLastIndex >= 0 {
        carray = carray + (bLastIndex >= 0 ? Int(String(b[b.index(b.startIndex, offsetBy: bLastIndex)]))! : 0)
        let tempString = String(carray % 2)
        result.insert(tempString[tempString.startIndex], at: result.startIndex)
        carray = carray >> 1
        bLastIndex -= 1
    }
    if carray > 0 {
        result.insert("1", at: result.startIndex)
    }
    
    return result
}

let a1 = "11", b1 = "1"
print("\(a1) + \(b1) = \(addBinary(a1, b1))")
let a2 = "1010", b2 = "1011"
print("\(a2) + \(b2) = \(addBinary(a2, b2))")
```


## 结语

如果你同我一样热爱数据结构、算法、LeetCode，可以关注我 GitHub 上的 LeetCode 题解：[awesome-swift-leetcode][zgpeace]



[title]: https://leetcode.com/problems/add-binary
[zgpeace]: https://github.com/zgpeace/awesome-swift-leetcode
