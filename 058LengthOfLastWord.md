# [Length of Last Word][title]

## Description

Given a string *s* consists of upper/lower-case alphabets and empty space characters `' '`, return the length of last word in the string.

If the last word does not exist, return 0.

**Note:** A word is defined as a character sequence consists of non-space characters only.

**Example:**

```
Input: "Hello World"
Output: 5
```

**Tags:** String


## 思路

题意是让你从一个只包含大小字母和空格字符的字符串中得到最后一个单词的长度，很简单，我们倒序遍历，先得到最后一个非空格字符的索引，然后再得到它前面的空格字符索引，两者相减即可。当然，我们使用 API 来完成这件事更加方便，只需一行代码 `return s.trim().length() - s.trim().lastIndexOf(" ") - 1;`，但我相信作者出这道题的目的肯定不是考你 API 的使用，所以我们还是用自己的思路来实现。

```swift
func lengthOfLastWord(_ s: String) -> Int {
    var lastIndex = s.count - 1
    while lastIndex >= 0 && s[s.index(s.startIndex, offsetBy: lastIndex)] == " " {
        lastIndex -= 1
    }
    let end = lastIndex
    while lastIndex >= 0 && s[s.index(s.startIndex, offsetBy: lastIndex)] != " " {
        lastIndex -= 1
    }
    
    return end - lastIndex
}
let input1 = "Hello World "
let input2 = "a"
print("input: \(input1), output: \(lengthOfLastWord(input1))")
print("input: \(input2), output: \(lengthOfLastWord(input2))")
```


## 结语

如果你同我一样热爱数据结构、算法、LeetCode，可以关注我 GitHub 上的 LeetCode 题解：[awesome-swift-leetcode][zgpeace]



[title]: https://leetcode.com/problems/length-of-last-word
[zgpeace]: https://github.com/zgpeace/awesome-swift-leetcode
