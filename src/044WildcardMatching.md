# [Wildcard Matching][title]

## Description

Given an input string (`s`) and a pattern (`p`), implement wildcard pattern matching with support for `'?'` and `'*'`.

```
'?' Matches any single character.
'*' Matches any sequence of characters (including the empty sequence).
```

The matching should cover the **entire** input string (not partial).

**Note:**

- `s` could be empty and contains only lowercase letters `a-z`.
- `p` could be empty and contains only lowercase letters `a-z`, and characters like `?` or `*`.

**Example 1:**

```
Input:
s = "aa"
p = "a"
Output: false
Explanation: "a" does not match the entire string "aa".
```

**Example 2:**

```
Input:
s = "aa"
p = "*"
Output: true
Explanation: '*' matches any sequence.
```

**Example 3:**

```
Input:
s = "cb"
p = "?a"
Output: false
Explanation: '?' matches 'c', but the second letter is 'a', which does not match 'b'.
```

**Example 4:**

```
Input:
s = "adceb"
p = "*a*b"
Output: true
Explanation: The first '*' matches the empty sequence, while the second '*' matches the substring "dce".
```

**Example 5:**

```
Input:
s = "acdcb"
p = "a*c?b"
Output: false
```

**Tags:** String, Dynamic Programming, Backtracking, Greedy


## 思路 0

题意是让让你从判断 `s` 字符串是否通配符匹配于 `p`，这道题和[Regular Expression Matching][010]很是相似，区别在于 `*`，正则匹配的 `*` 不能单独存在，前面必须具有一个字符，其意义是表明前面的这个字符个数可以是任意个数，包括 0 个；而通配符的 `*` 是可以随意出现的，跟前面字符没有任何关系，其作用是可以表示任意字符串。在此我们可以利用 *贪心算法* 来解决这个问题，需要两个额外指针 `p` 和 `match` 来分别记录最后一个 `*` 的位置和 `*` 匹配到 `s` 字符串的位置，其贪心体现在如果遇到 `*`，那就尽可能取匹配后方的内容，如果匹配失败，那就回到上一个遇到 `*` 的位置来继续贪心。

```swfit
class Solution {
    func isMatch(_ s: String, _ p: String) -> Bool {
        //1. greedy
        return isMatchByGreedy(s, p)
    }
    
    func isMatchByGreedy(_ s: String, _ p: String) -> Bool {
        if p.isEmpty {
            return s.isEmpty
        }
        let slen = s.count
        let plen = p.count
        var sindex = 0
        var pindex = 0
        var smatch = 0
        var pstar = -1
        while sindex < slen {

            if pindex < plen && (p[p.index(p.startIndex, offsetBy: pindex)] == s[s.index(s.startIndex, offsetBy: sindex)] || p[p.index(p.startIndex, offsetBy: pindex)] == "?") {
                sindex += 1
                pindex += 1
            } else if pindex < plen && p[p.index(p.startIndex, offsetBy: pindex)] == "*" {
                smatch = sindex
                pstar = pindex
                pindex += 1
            } else if pstar != -1 {
                smatch += 1
                sindex = smatch
                pindex = pstar + 1
            } else {
                return false
            }
        }

        while pindex < plen && p[p.index(p.startIndex, offsetBy: pindex)] == "*" {
            pindex += 1
        }

        return pindex == plen
    }
}
```

## 结语

如果你同我一样热爱数据结构、算法、LeetCode，可以关注我 GitHub 上的 LeetCode 题解：[awesome-swfit-leetcode][zgpeace]



[010]: https://github.com/zgpeace/awesome-swift-leetcode/blob/master/src/010RegularExpressionMatching.md
[title]: https://leetcode.com/problems/wildcard-matching
[zgpeace]: https://github.com/zgpeace/awesome-swift-leetcode
