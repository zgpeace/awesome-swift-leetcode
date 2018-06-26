# [Roman to Integer][title]

## Description

Roman numerals are represented by seven different symbols: `I`, `V`, `X`, `L`, `C`, `D` and `M`.

```
Symbol       Value
I             1
V             5
X             10
L             50
C             100
D             500
M             1000
```

For example, two is written as `II` in Roman numeral, just two one's added together. Twelve is written as, `XII`, which is simply `X` + `II`. The number twenty seven is written as `XXVII`, which is `XX` + `V` + `II`.

Roman numerals are usually written largest to smallest from left to right. However, the numeral for four is not `IIII`. Instead, the number four is written as `IV`. Because the one is before the five we subtract it making four. The same principle applies to the number nine, which is written as `IX`. There are six instances where subtraction is used:

- `I` can be placed before `V` (5) and `X` (10) to make 4 and 9. 
- `X` can be placed before `L` (50) and `C` (100) to make 40 and 90. 
- `C` can be placed before `D` (500) and `M` (1000) to make 400 and 900.

Given a roman numeral, convert it to an integer. Input is guaranteed to be within the range from 1 to 3999.

**Example 1:**

```
Input: "III"
Output: 3
```

**Example 2:**

```
Input: "IV"
Output: 4
```

**Example 3:**

```
Input: "IX"
Output: 9
```

**Example 4:**

```
Input: "LVIII"
Output: 58
Explanation: C = 100, L = 50, XXX = 30 and III = 3.
```

**Example 5:**

```
Input: "MCMXCIV"
Output: 1994
Explanation: M = 1000, CM = 900, XC = 90 and IV = 4.
```

**Tags:** Math, String


## 思路

题意是罗马数字转整型数，范围从 1 到 3999，查看下百度百科的罗马数字介绍如下：

* 相同的数字连写，所表示的数等于这些数字相加得到的数，如 Ⅲ=3；

* 小的数字在大的数字的右边，所表示的数等于这些数字相加得到的数，如 Ⅷ=8、Ⅻ=12；

* 小的数字（限于 Ⅰ、X 和 C）在大的数字的左边，所表示的数等于大数减小数得到的数，如 Ⅳ=4、Ⅸ=9。

那么我们可以利用 map 来完成罗马数字的 7 个数字符号：I、V、X、L、C、D、M 和整数的映射关系，然后根据上面的解释来模拟完成即可。

```swift
func romanToInt(_ s: String) -> Int {
    let romanIntegerMap: [Character: Int] = ["I": 1, "V": 5, "X": 10, "L": 50, "C": 100, "D": 500, "M": 1000]
    let len = s.count
    if len == 0 {
        return 0
    }
    let lastIndex = s.index(s.startIndex, offsetBy: len - 1)
    let lastChar: Character = s[lastIndex]
    var sum:Int = romanIntegerMap[lastChar]!
    
    var lenCopy = len - 2
    while lenCopy >= 0 {
        let beforeIndex = lenCopy + 1
        let currenChar: Character = s[s.index(s.startIndex, offsetBy: lenCopy)]
        let beforeChar: Character = s[s.index(s.startIndex, offsetBy: beforeIndex)]
        if romanIntegerMap[currenChar]! >= romanIntegerMap[beforeChar]! {
            sum = sum + romanIntegerMap[currenChar]!
        } else {
            sum = sum - romanIntegerMap[currenChar]!
        }
        lenCopy = lenCopy - 1
    }

    return sum
}

let input1 = "III"
let input2 = "IV"
let input3 = "IX"
let input4 = "LVIII"
let input5 = "MCMXCIV"

print("input: \(input1), output: \(romanToInt(input1))" )
print("input: \(input2), output: \(romanToInt(input2))" )
print("input: \(input3), output: \(romanToInt(input3))" )
print("input: \(input4), output: \(romanToInt(input4))" )
print("input: \(input5), output: \(romanToInt(input5))" )
```


## 结语

如果你同我一样热爱数据结构、算法、LeetCode，可以关注我 GitHub 上的 LeetCode 题解：[awesome-swift-leetcode][zgpeace]



[title]: https://leetcode.com/problems/roman-to-integer
[zgpeace]: https://github.com/zgpeace/awesome-swift-leetcode
