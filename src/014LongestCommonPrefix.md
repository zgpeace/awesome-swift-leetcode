# [Longest Common Prefix][title]

## Description

Write a function to find the longest common prefix string amongst an array of strings.

If there is no common prefix, return an empty string `""`.

**Example 1:**

```
Input: ["flower","flow","flight"]
Output: "fl"
```

**Example 2:**

```
Input: ["dog","racecar","car"]
Output: ""
Explanation: There is no common prefix among the input strings.
```

**Note:**

All given inputs are in lowercase letters `a-z`.

**Tags:** String


## 思路

题意是让你从字符串数组中找出公共前缀，我的想法是找出最短的那个字符串的长度 `minLen`，然后在 `0...minLen` 的范围比较所有字符串，如果比较到有不同的字符，那么直接返回当前索引长度的字符串即可，否则最后返回最短的字符串即可。

```swift
func longestCommonPrefix(_ strs: [String]) -> String {
    let len = strs.count
    if len == 0 {
        return ""
    }
    var minLength:Int = Int.max
    for item in strs {
        minLength = min(minLength, item.count)
    }
    if minLength == 0 {
        return ""
    }
    
    let fistString = strs[0]
    for j in 0..<minLength  {
        for i in 1..<len{
            let currenString = strs[i]
            let fisrtStringChar: Character = fistString[fistString.index(fistString.startIndex, offsetBy: j)]
            let currentStringChar: Character = currenString[currenString.index(currenString.startIndex, offsetBy: j)]
            if fisrtStringChar != currentStringChar {
                return String(fistString.prefix(j))
            }
            
        }
    }
    
    return String(fistString.prefix(minLength))
}

//let input: [String] = ["flower","flow","flight"]
//let input: [String] = ["flow1","flow3","flow"]
let input: [String] = ["abca","aba","aaab"]
let result = longestCommonPrefix(input)
print("result: \(result)")
```


## 结语

如果你同我一样热爱数据结构、算法、LeetCode，可以关注我 GitHub 上的 LeetCode 题解：[awesome-swift-leetcode][zgpeace]



[title]: https://leetcode.com/problems/longest-common-prefix
[zgpeace]: https://github.com/zgpeace/awesome-swift-leetcode
