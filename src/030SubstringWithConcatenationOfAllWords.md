# [Substring with Concatenation of All Words][title]

## Description

You are given a string, **s**, and a list of words, **words**, that are all of the same length. Find all starting indices of substring(s) in **s** that is a concatenation of each word in **words** exactly once and without any intervening characters.

**Example 1:**

```
Input:
  s = "barfoothefoobarman",
  words = ["foo","bar"]
Output: [0,9]
Explanation: Substrings starting at index 0 and 9 are "barfoor" and "foobar" respectively.
The output order does not matter, returning [9,0] is fine too.
```

**Example 2:**

```
Input:
  s = "wordgoodstudentgoodword",
  words = ["word","student"]
Output: []
```

**Tags:** Hash Table, Two Pointers, String


## 思路 0
遍历string的字符串，挨个匹配，O(n*wordLength)

**暴力破解之 (LeetCode 运行不过，原因：Time Limit Exceeded)**

1. 使用HashMap来保存L中所有的字串。

2. 暴力破解之。使用i记录我们的查找结果字符串的位置，j记录单个单词的查找位置。j每次移动一个L中单词的位置。

3. 注意各种越界条件：i查到离结束还有L*N（L中所有单词总长）的时候，即需要停止。

    j 也要考虑每一次查找的单词的长度。

4. 使用第二个HashMap来记录我们查到的单词。如果所有的单词都查到了，即可记录一个解。

```swift
func findSubStringByIterate(_ s: String, _ words: [String]) -> [Int] {
    var resultList: [Int] = [Int]()
    if s.count == 0 || words.count == 0 {
        return resultList
    }
    let wordLen = words.first!.count
    let wordsCount = words.count
    let matchLen = wordLen * wordsCount
    
    if s.count < matchLen {
        return resultList
    }
    var wordDict: [String: Int] = [String: Int]()
    var foundDict: [String: Int] = [String: Int]()
    for word in words {
        if let _ = wordDict[word] {
            wordDict[word]! += 1
        } else {
            wordDict[word] = 1
        }
    }
    
    for i in 0...(s.count - matchLen) {
        foundDict.removeAll()
        var foundCount: Int = 0
        
        for j in 0..<wordsCount {
            let startIndex = s.index(s.startIndex, offsetBy: i + wordLen * j)
            let endIndex = s.index(s.startIndex, offsetBy: i + wordLen * (j + 1))
            let tempWord = String(s[startIndex..<endIndex])
            if let _ = wordDict[tempWord] {
                if let _ = foundDict[tempWord] {
                    if foundDict[tempWord]! == wordDict[tempWord]! {
                        break;
                    }
                    foundDict[tempWord]! += 1
                } else {
                    foundDict[tempWord] = 1
                }
                
                foundCount += 1
            } else {
                break
            }
        }
        
        if foundCount == wordsCount {
            resultList.append(i)
        }
    }
    
    return resultList
}

```

## 思路 1
通过滑动窗口的思维，窗口大小为words数组的1个单位。

An O(N) solution with detailed explanation

1. travel all the words combinations to maintain a window

2. there are wl(word len) times travel

3. each time, n/wl words, mostly 2 times travel for each word

4. one left side of the window, the other right side of the window

5. so, time complexity O(wl * 2 * N/wl) = O(2N)


```swift
func findSubStringBySlideWindow(_ s: String, _ words: [String]) -> [Int] {
    var resultList: [Int] = [Int]()
    if s.count == 0 || words.count == 0 {
        return resultList
    }
    let wordLen = words.first!.count
    let wordsCount = words.count
    let matchLen = wordLen * wordsCount
    
    if s.count < matchLen {
        return resultList
    }
    var wordDict: [String: Int] = [String: Int]()
    var foundDict: [String: Int] = [String: Int]()
    var distinguishCount: Int = 0
    for word in words {
        if let _ = wordDict[word] {
            wordDict[word]! += 1
        } else {
            wordDict[word] = 1
            distinguishCount += 1
        }
    }
    
    for k in 0..<wordLen {
        foundDict.removeAll()
        var foundTotal: Int = 0
        var i = k
        var j = k
        while j <= s.count - wordLen {
            if j - i >= matchLen {
                let startIndexI = s.index(s.startIndex, offsetBy: i)
                let endIndexI = s.index(s.startIndex, offsetBy: i + wordLen)
                let tempWord = String(s[startIndexI..<endIndexI])
                if let standardCount = wordDict[tempWord] {
                    if let foundCount = foundDict[tempWord] {
                        if standardCount == foundCount {
                            foundTotal -= 1
                        }
                        foundDict[tempWord]! -= 1
                    }
                }
                
                i += wordLen
            }
            
            let startIndexJ = s.index(s.startIndex, offsetBy: j)
            let endIndexJ = s.index(s.startIndex, offsetBy: j + wordLen)
            let tempWordJ = String(s[startIndexJ..<endIndexJ])
            if let _ = wordDict[tempWordJ] {
                if let _ = foundDict[tempWordJ] {
                    foundDict[tempWordJ]! += 1
                } else {
                    foundDict[tempWordJ] = 1
                }
                
                if wordDict[tempWordJ] == foundDict[tempWordJ] {
                    foundTotal += 1
                }
            }
            
            if foundTotal == distinguishCount {
                resultList.append(i)
            }
            
            j += wordLen
        }
        
    }
    
    return resultList
}

```


## 结语

如果你同我一样热爱数据结构、算法、LeetCode，可以关注我 GitHub 上的 LeetCode 题解：[awesome-swift-leetcode][zgpeace]



[title]: https://leetcode.com/problems/substring-with-concatenation-of-all-words
[zgpeace]: https://github.com/zgpeace/awesome-swift-leetcode
