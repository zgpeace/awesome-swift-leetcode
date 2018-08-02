# [Letter Combinations of a Phone Number][title]

## Description

Given a digit string, return all possible letter combinations that the number could represent.

A mapping of digit to letters (just like on the telephone buttons) is given below.

![img](https://upload.wikimedia.org/wikipedia/commons/thumb/7/73/Telephone-keypad2.svg/200px-Telephone-keypad2.svg.png)

**Example:**

```
Input: "23"
Output: ["ad", "ae", "af", "bd", "be", "bf", "cd", "ce", "cf"].
```

**Note:**

Although the above answer is in lexicographical order, your answer could be in any order you want.

**Tags:** String, Backtracking


## 思路 0

题意是给你按键，让你组合出所有不同结果，首先想到的肯定是回溯了，对每个按键的所有情况进行回溯，回溯的终点就是结果字符串长度和按键长度相同。

```swift
class Solution {
    let lettersArray:[String] = ["abc", "def", "ghi", "jkl", "mno", "pqrs", "tuv", "wxyz"]

    func letterCombinations(_ digits: String) -> [String] {
        
        //method 1: backtracking best
        var resultArray: [String] = [String]()
        let len = digits.count

        if len == 0 {
            return resultArray
        }

        helper(&resultArray, digits, "")

        return resultArray
    }

    func helper(_ list:inout [String], _ digits: String, _ letter: String) {
        if digits.count == letter.count {
            list.append(letter)
            return
        }
        let twoUnicode: Int = Int("2".unicodeScalars.first!.value)
        let letterUnicode: Int = Int(digits[digits.index(digits.startIndex, offsetBy: letter.count)].unicodeScalars.first!.value)
        let index : Int = letterUnicode - twoUnicode;

        for c in lettersArray[index] {
            helper(&list, digits, letter + String(c))
        }
    }
}
```

## 思路 1

还有一种思路就是利用队列，根据上一次队列中的值，该值拼接当前可选值来不断迭代其结果，具体代码如下。

```swift
class Solution {
    let lettersArray:[String] = ["abc", "def", "ghi", "jkl", "mno", "pqrs", "tuv", "wxyz"]

    func letterCombinations(_ digits: String) -> [String] {
        //method 2: queue
        var resultArray: [String] = [String]()
        let len = digits.count

        if len == 0 {
            return resultArray
        }
        resultArray.append("")

        let twoUnicode: Int = Int("2".unicodeScalars.first!.value)

        for (i, digitScalar) in digits.unicodeScalars.enumerated() {
            while resultArray.first!.count == i {
                let item = resultArray.removeFirst()
                for c in lettersArray[Int(digitScalar.value) - twoUnicode] {
                    resultArray.append(item + String(c))
                }
            }
        }

        return resultArray
    }
}
```


## 结语

如果你同我一样热爱数据结构、算法、LeetCode，可以关注我 GitHub 上的 LeetCode 题解：[awesome-swift-leetcode][zgpeace]



[title]: https://leetcode.com/problems/letter-combinations-of-a-phone-number
[zgpeace]: https://github.com/zgpeace/awesome-swift-leetcode
