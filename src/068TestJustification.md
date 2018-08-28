# [Text Justification][title]

## Description

Given an array of words and a width *maxWidth*, format the text such that each line has exactly *maxWidth* characters and is fully (left and right) justified.

You should pack your words in a greedy approach; that is, pack as many words as you can in each line. Pad extra spaces `' '` when necessary so that each line has exactly *maxWidth* characters.

Extra spaces between words should be distributed as evenly as possible. If the number of spaces on a line do not divide evenly between words, the empty slots on the left will be assigned more spaces than the slots on the right.

For the last line of text, it should be left justified and no **extra** space is inserted between words.

**Note:**

- A word is defined as a character sequence consisting of non-space characters only.
- Each word's length is guaranteed to be greater than 0 and not exceed *maxWidth*.
- The input array `words` contains at least one word.

**Example 1:**

```
Input:
words = ["This", "is", "an", "example", "of", "text", "justification."]
maxWidth = 16
Output:
[
   "This    is    an",
   "example  of text",
   "justification.  "
]
```

**Example 2:**

```
Input:
words = ["What","must","be","acknowledgment","shall","be"]
maxWidth = 16
Output:
[
  "What   must   be",
  "acknowledgment  ",
  "shall be        "
]
Explanation: Note that the last line is "shall be    " instead of "shall     be",
             because the last line must be left-justified instead of fully-justified.
             Note that the second line is also left-justified becase it contains only one word.
```

**Example 3:**

```
Input:
words = ["Science","is","what","we","understand","well","enough","to","explain",
         "to","a","computer.","Art","is","everything","else","we","do"]
maxWidth = 20
Output:
[
  "Science  is  what we",
  "understand      well",
  "enough to explain to",
  "a  computer.  Art is",
  "everything  else  we",
  "do                  "
]
```

**Tags:** String


## 思路

题意是给你一组单词和最大行宽，让你对齐他们，对齐的规则就是尽可能一行可以放下足够多的单词，如果最后有多余的空格，那就把空格均匀地插入到单词之间，如果不能平分的话，那就从左开始依次多插一个空格，最后一行单词之间就正常地一个空格即可，如果凑不到最大行宽，那就在末尾补充空格即可，描述地比较差，不懂的话其实看看 demo 也就懂了哈。题还是比较坑的，毕竟踩的比赞的人多，我也是靠模拟老老实实做出来的，求出可以最多插入空格数，然后用它除以可以插入的槽数获取每个单词之间的空格，它两取余的话就是最面需要多插入一个空格的个数，最后一行的话就单独处理即可。

```swift
class Solution {
    func fullJustify(_ words: [String], _ maxWidth: Int) -> [String] {
        var resultList: [String] = [String]()
        let wordsLen: Int = words.count
        var blankString: String = ""
        for _ in 0..<maxWidth {
            blankString.append(" ")
        }
        var startIndex: Int = 0
        var currentLineLength: Int = -1
        let minBlank: Int = 1

        //normal line
        for i in 0..<wordsLen {
            //line length <= maxWidth
            if currentLineLength + words[i].count + minBlank <= maxWidth {
                currentLineLength += words[i].count + minBlank
            } else {
                var currentLine: String = words[startIndex]
                let holeNumber = i - 1 - startIndex //i is exclude
                let restBlanks: Int = maxWidth - currentLineLength

                //one word
                if holeNumber <= 0 {
                    currentLine += blankString[..<blankString.index(blankString.startIndex, offsetBy: restBlanks)]
                } else {
                    //more than one word
                    let blanksPerLine: Int = (restBlanks / holeNumber) + minBlank
                    var remainderBlanks: Int = restBlanks % holeNumber
                    var j = startIndex + 1
                    while j < i {
                        if remainderBlanks > 0 {
                            //left string add more one blank
                            currentLine += blankString[..<blankString.index(blankString.startIndex, offsetBy: blanksPerLine + 1)] + words[j]
                            remainderBlanks -= 1
                        } else {
                            currentLine += blankString[..<blankString.index(blankString.startIndex, offsetBy: blanksPerLine)] + words[j]
                        }

                        j += 1
                    }


                }

                //update data
                resultList.append(currentLine)
                startIndex = i
                currentLineLength = words[i].count
            }
        }

        //last line
        var lastLine: String = words[startIndex]
        var k: Int = startIndex + 1
        while k < wordsLen {
            lastLine += " " + words[k]
            k += 1
        }
        let restBlank = maxWidth - lastLine.count
        if restBlank > 0 {
            lastLine += blankString[..<blankString.index(blankString.startIndex, offsetBy: restBlank)]
        }
        //add line
        resultList.append(lastLine)

        return resultList
    }
}
```


## 结语

如果你同我一样热爱数据结构、算法、LeetCode，可以关注我 GitHub 上的 LeetCode 题解：[awesome-swift-leetcode][zgpeace]



[title]: https://leetcode.com/problems/text-justification
[zgpeace]: https://github.com/zgpeace/awesome-swift-leetcode
