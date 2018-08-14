# [Group Anagrams][title]

## Description

Given an array of strings, group anagrams together.

**Example:**

```
Input: ["eat", "tea", "tan", "ate", "nat", "bat"],
Output:
[
  ["ate","eat","tea"],
  ["nat","tan"],
  ["bat"]
]
```

**Note:**

- All inputs will be in lowercase.
- The order of your output does not matter.

**Tags:** Hash Table, String


## 思路

题意是给你一组字符串，让你把其中同位异构字符串分组，同位异构字符串就是组成字符串的字符都相同，但是字符放的位置可以不同。既然要分组，那么关键就是如何确定他们是同位异构字符串呢，想到的自然就是对其排序，排序之后他们就都是同一个字符串了，就可以归为一类了，代码如下所示。

```swift
class Solution {
    func groupAnagrams(_ strs: [String]) -> [[String]] {
        var dic: [String: Int] = [String: Int]()
        var list: [[String]] = [[String]]()
        var i: Int = 0
        for item in strs {
            let sortItem: String = String(item.sorted())
            if let index = dic[sortItem] {
                list[index].append(item)
            } else {
                dic[sortItem] = i
                var subList: [String] = [String]()
                subList.append(item)
                list.append(subList)
                i += 1
            }
        }

        return list
    }
}
```


## 结语

如果你同我一样热爱数据结构、算法、LeetCode，可以关注我 GitHub 上的 LeetCode 题解：[awesome-swift-leetcode][zgpeace]



[title]: https://leetcode.com/problems/group-anagrams
[zgpeace]: https://github.com/zgpeace/awesome-swift-leetcode
