# [Count and Say][title]

## Description

The count-and-say sequence is the sequence of integers with the first five terms as following:

```
1.     1
2.     11
3.     21
4.     1211
5.     111221
```

`1` is read off as `"one 1"` or `11`.

`11` is read off as `"two 1s"` or `21`.

`21` is read off as `"one 2`, then `one 1"` or `1211`.

Given an integer *n*, generate the *n*<sup>th</sup> term of the count-and-say sequence.

Note: Each term of the sequence of integers will be represented as a string.

**Example 1:**

```
Input: 1
Output: "1"
```

**Example 2:**

```
Input: 4
Output: "1211"
```

**Tags:** String


## 思路

题意是数和说，根据如下序列 `1, 11, 21, 1211, 111221, ...`，求第 n 个数，规则很简单,就是数和说，数就是数这个数数字有几个，说就是说这个数，所以 `1` 就是 1 个 1：`11`,`11` 就是有 2 个 1：`21`，`21` 就是 1 个 2、1 个 1：`1211`，可想而知后面就是 `111221`，思路的话就是按这个逻辑模拟出来即可。

```swift
func countAndSay(_ n: Int) -> String {
    var n = n
    if n == 0 {
        return ""
    }
    var str = "1"
    n -= 1
    while n > 0 {
        var times = 1
        var tempStr = String()
        
        for index in str.indices {
            if index == str.startIndex {
                continue
            }
            if str[index] == str[str.index(before: index)] {
                times += 1
            } else {
                tempStr = tempStr + String(times)
                tempStr.append(str[str.index(before: index)])
                times = 1
            }
        }
        
        tempStr = tempStr + String(times)
        tempStr.append(str[str.index(before: str.endIndex)])
        str = String(tempStr)
        
        n -= 1
    }
    
    return str
}
let input1 = 1
let input2 = 2
let input3 = 3
let input4 = 4
let input5 = 5
print("input: \(input1), output: \(countAndSay(input1))")
print("input: \(input2), output: \(countAndSay(input2))")
print("input: \(input3), output: \(countAndSay(input3))")
print("input: \(input4), output: \(countAndSay(input4))")
print("input: \(input5), output: \(countAndSay(input5))")
```


## 结语

如果你同我一样热爱数据结构、算法、LeetCode，可以关注我 GitHub 上的 LeetCode 题解：[awesome-swift-leetcode][zgpeace]



[title]: https://leetcode.com/problems/count-and-say
[zgpeace]: https://github.com/zgpeace/awesome-swift-leetcode
