# [Longest Palindromic Substring][title]

## Description

Given a string **s**, find the longest palindromic substring in **s**. You may assume that the maximum length of **s** is 1000.

**Example 1:**

```
Input: "babad"

Output: "bab"

Note: "aba" is also a valid answer.
```

**Example 2:**

```
Input: "cbbd"

Output: "bb"
```

**Tags:** String, Dynamic Programming


## 思路 0

题意是寻找出字符串中最长的回文串，所谓回文串就是正序和逆序相同的字符串，也就是关于中间对称。我们先用最常规的做法，依次去求得每个字符的最长回文，要注意每个字符有奇数长度的回文串和偶数长度的回文串两种情况，相信你可以很轻易地从如下代码中找到相关代码，记录最长回文的始末位置即可，时间复杂度的话，首先要遍历一遍字符串，然后对每个字符都去求得最长回文，所以时间复杂度为 `O(n^2)`。

```swift
var startIndex = 0
var endIndex = 0
func longestPalindrome(_ s: String) -> String {
    let length = s.count
    if length <= 1 {
        return s
    }
    for item in 0..<length {
        palindromeHelper(s, item, item)
        palindromeHelper(s, item, item+1)
    }
    
    let firstIndex = s.index(s.startIndex, offsetBy: startIndex)
    let secondIndex = s.index(s.startIndex, offsetBy: endIndex)
    return String(s[firstIndex...secondIndex])
}

func palindromeHelper(_ s: String, _ leftInt: Int, _ rightInt: Int) {
    let length = s.count
    var leftVarInt = leftInt
    var rightVarInt = rightInt
    while leftVarInt >= 0 && rightVarInt < length && s[s.index(s.startIndex, offsetBy: leftVarInt)] == s[s.index(s.startIndex, offsetBy: rightVarInt)] {
        leftVarInt -= 1
        rightVarInt += 1
    }
    if endIndex - startIndex < rightVarInt - leftVarInt - 2 {
        startIndex = leftVarInt + 1
        endIndex = rightVarInt - 1
    }
}
```


## 思路 1

如果利用暴力法遍历所有字串是否回文的情况这道题肯定是 `Time Limit Exceeded` 的，那么我们是否可以把之前遍历的结果利用上呢，那么动态规划的想法就呼之欲出了，我们定义 `dp[i][j]` 的意思为字符串区间 `[i, j]` 是否为回文串，那么我们分三种情况：

1. 当 `i == j` 时，那么毫无疑问 `dp[i][j] = true`；

2. 当 `i + 1 == j` 时，那么 `dp[i][j]` 的值取决于 `s[i] == s[j]`；

3. 当 `i + 1 < j` 时，那么 `dp[i][j]` 的值取决于 `dp[i + 1][j - 1] && s[i] == s[j]`。

根据以上的动态转移方程，我们的问题即可迎刃而解，时间复杂度的话显而易见，也是 `O(n^2)`。

```swift
func longestPalindromeWithDynamic(_ s: String) -> String {
    var startIndex = 0
    var endIndex = 0
    
    let length = s.count
    if length <= 1 {
        return s
    }
    var zoomFlag = Array(repeating: Array(repeating: false, count: length), count: length)
    
    zoomFlag[1][1] = true
    for i in 0..<length {
        zoomFlag[i][i] = true
        for j in 0..<i {
            if (j + 1) == i {
                zoomFlag[j][i] = s[s.index(s.startIndex, offsetBy: j)] == s[s.index(s.startIndex, offsetBy: i)]
            } else {
                zoomFlag[j][i] = zoomFlag[j + 1][i - 1] && s[s.index(s.startIndex, offsetBy: j)] == s[s.index(s.startIndex, offsetBy: i)]
            }
            if zoomFlag[j][i] && endIndex - startIndex < i - j {
                startIndex = j
                endIndex = i
            }
        }
    }

    let firstIndex = s.index(s.startIndex, offsetBy: startIndex)
    let secondIndex = s.index(s.startIndex, offsetBy: endIndex)
    return String(s[firstIndex...secondIndex])
}
```


## 思路 2

马拉车算法(Manacher's Algorithm)

### 背景

给定一个字符串，求出其最长回文子串（回文字符串就是从左到右读和从右往左读完全一样，也就是字符串关于中间对称）。例如：

1. s = "babad"，最长回文长度为 `3`，可以是 `bab` 或者 `aba`；

2. s = "cbbda"，最长回文长度为 `2`，即 `bb`；

3. s = "abcde"，最长回文长度为 `1`，即单个字符本身。

参考文章 中文： [Manacher 算法及其 Java 实现](https://juejin.im/entry/58c7936944d90400699c2db4)，  
English：[Manacher's Algorithm explanation and code in Java](http://hanslen.me/2017/07/28/Manacher-s-Algorithm-explanation-and-code-with-java/)

以上问题的传统思路大概是遍历每一个字符，以该字符为中心向两边查找，其时间复杂度为 `O(n^2)`，效率很差。

1975 年，一个叫 Manacher 的人发明了 Manacher 算法（中文名：马拉车算法），该算法可以把时间复杂度提升到 `O(n)`，下面我以我理解的思路来讲解其原理。


### 分析

由于回文串的奇偶行不确定，比如 `lol` 是奇回文，而 `lool` 是偶回文，马拉车算法的第一步就是对其进行预处理，做法就是在每个字符两侧都加上一个特殊字符，一般就是不会出现在原串中的即可，我们可以选取 `#`，那么

```
lol  -> #l#o#l#
lool -> #l#o#o#l#
```

这样处理后，不管原来字符串长度是奇数还是偶数，最终得到的长度都将是奇数，从而能把两种情况合并起来一起考虑，记预处理后的字符串为 `str`。

我们把一个回文串中最左或最右位置的字符与其对称轴的距离称为回文半径。

马拉车算法定义了一个回文半径数组 `len`，用 `len[i]` 表示以第 `i` 个字符为对称轴的回文串的回文半径，比如以 `str[i]` 为中心的最长回文串是 `str[l, r]`，那么 `len[i] = r - i + 1`

我们以 `lollool` 为例，参看下表。

| str   | #    | l    | #    | o    | #    | l    | #    | l    | #    | o    | #    | o    | #    | l    | #    |
| :---  | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| len[] | 1    | 2    | 1    | 4    | l    | 2    | 5    | 2    | 1    | 2    | 5    | 2    | 1    | 2    | 1    |

可以发现 `len[i] - 1` 就等于该回文串在原串中的长度。

证明：在转换后的字符串 `str` 中，那么对于以 `str[i]` 为中心的最长回文串的长度为 `2 * len[i] - 1`，其中又有 `len[i]` 个分隔符，所以在原字符串中的回文串长度就是 `len[i] - 1`。

那么我们剩下的工作就是求 `len` 数组。

```swift
func longestPalindromeWithManacher(_ s: String) -> String {
    let length = s.count
    if length <= 1 {
        return s
    }
    //1. 构造新的字符串
    var newString:String = "#"
    
    //为了避免奇数回文和偶数回文的不同处理问题，在原字符串中出入'#'，将所有回文变成奇数回文
    let separateChar:Character = "#"
    
    for item in s {
        newString.append(item)
        newString.append(separateChar)
    }
    let newLength = newString.count
    //radius[i]表示以i为中心的回文的最大半径，radius至少为1，即该字符本身
    var radius:[Int] = [Int](repeating: 1, count: newLength)
    //right表示已知的回文中，最右边的边界的坐标
    var rightMax = -1
    var middleId = -1
    
    var startIndex = 0
    var endIndex = 0
    var maxLength = -1
    //2. 计算所有的radius
    //这个算法是O(n)的，因为right只会随着里层while的迭代而增加，不会减少
    for i in 1..<(newLength-1) {
        //2.1. 确定一个最小的半径
        var r = 1
        if i <= rightMax {
            r = min(radius[middleId] - (i - middleId), radius[middleId - (i - middleId)])
        }
        
        //2.2. 尝试更大的半径
        while (i - r >= 0) && (i + r < newLength) && (newString[newString.index(newString.startIndex, offsetBy: i - r)] == newString[newString.index(newString.startIndex, offsetBy: i + r)]) {
            r += 1
        }
        //2.3. 更新边界和回文中心坐标
        if i + r - 1 > rightMax {
            rightMax = i + r - 1
            middleId = i
        }
        
        radius[i] = max(1, r - 1) ;
        
        //3. 扫描一遍radius数组，找出最大的半径
        let val = radius[i]
        if val > maxLength {
            maxLength = val
            let newLeft = i - (maxLength - 1)
            startIndex = newLeft / 2
            endIndex = startIndex + maxLength - 1
        }
    }
    
    let firstIndex = s.index(s.startIndex, offsetBy: startIndex)
    let secondIndex = s.index(s.startIndex, offsetBy: endIndex)
    return String(s[firstIndex...secondIndex])
}

```



## 结语

如果你同我一样热爱数据结构、算法、LeetCode，可以关注我 GitHub 上的 LeetCode 题解：[awesome-swift-leetcode][zgpeace]



[title]: https://leetcode.com/problems/longest-palindromic-substring
[zgpeace]: https://github.com/zgpeace/awesome-swift-leetcode
