# [Implement strStr()][title]

## Description

Implement [strStr()](http://www.cplusplus.com/reference/cstring/strstr/).

Return the index of the first occurrence of needle in haystack, or **-1** if needle is not part of haystack.

**Example 1:**

```
Input: haystack = "hello", needle = "ll"
Output: 2
```

**Example 2:**

```
Input: haystack = "aaaaa", needle = "bba"
Output: -1
```

**Clarification:**

What should we return when `needle` is an empty string? This is a great question to ask during an interview.

For the purpose of this problem, we will return 0 when `needle` is an empty string. This is consistent to C's [strstr()](http://www.cplusplus.com/reference/cstring/strstr/) and Java's [indexOf()](https://docs.oracle.com/javase/7/docs/api/java/lang/String.html#indexOf(java.lang.String)).

Tags:** Two Pointers, String


## 思路

题意是从主串中找到子串的索引，如果找不到则返回-1，当子串长度大于主串，直接返回-1，然后我们只需要遍历比较即可。

```swift
func strStr(_ haystack: String, _ needle: String) -> Int {
    let haystackLen = haystack.count
    let needleLen = needle.count
    if haystackLen < needleLen {
        return -1
    }
    for i in 0...Int.max {
        if (i + needleLen) > haystackLen {
            return -1
        }
        for j in 0...Int.max {
            if j == needleLen {
                return i
            }
            
            let hayChar = haystack[haystack.index(haystack.startIndex, offsetBy: (i+j))]
            let needleChar = needle[needle.index(needle.startIndex, offsetBy: j)]
            if hayChar != needleChar{
                break;
            }
        }
    }
    
    return -1
}

let haystack1 = "hello", needle1 = "ll"
print("haystack: \(haystack1); needle: \(needle1); result: \(strStr(haystack1, needle1))")
let haystack2 = "aaaaa", needle2 = "bba"
print("haystack: \(haystack2); needle: \(needle2); result: \(strStr(haystack2, needle2))")
```


## 结语

如果你同我一样热爱数据结构、算法、LeetCode，可以关注我 GitHub 上的 LeetCode 题解：[awesome-swift-leetcode][zgpeace]



[title]: https://leetcode.com/problems/implement-strstr
[zgpeace]: https://github.com/zgpeace/awesome-swift-leetcode
