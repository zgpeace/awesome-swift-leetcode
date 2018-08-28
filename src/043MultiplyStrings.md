# [Multiply Strings][title]

## Description

1. Given two non-negative integers `num1` and `num2` represented as strings, return the product of `num1` and `num2`, also represented as a string.

   **Example 1:**

   ```
   Input: num1 = "2", num2 = "3"
   Output: "6"
   ```

   **Example 2:**

   ```
   Input: num1 = "123", num2 = "456"
   Output: "56088"
   ```

   **Note:**

   1. The length of both `num1` and `num2` is < 110.
   2. Both `num1` and `num2` contain only digits `0-9`.
   3. Both `num1` and `num2` do not contain any leading zero, except the number 0 itself.
   4. You **must not use any built-in BigInteger library** or **convert the inputs to integer** directly.

**Tags:** Math, String


## 思路

题意是让你计算两个非负字符串的乘积，我们模拟小学数学的方式来做，一位一位模拟计算，再各位累加。

```swift
class Solution {
    func multiply(_ num1: String, _ num2: String) -> String {
        if num1 == "0" || num2 == "0" {
            return "0"
        }
        let l1 = num1.count
        let l2 = num2.count
        let l = l1 + l2
        var sumArray: [Int] = [Int](repeating: 0, count: l)
        let zeroUnicode:Int = Int("0".unicodeScalars.first!.value)
        let unicodeScalars1 = num1.unicodeScalars
        let unicodeScalars2 = num2.unicodeScalars

        var i1 = l1 - 1
        while i1 >= 0 {
            var i2 = l2 - 1
            let item1 = Int(unicodeScalars1[unicodeScalars1.index(unicodeScalars1.startIndex, offsetBy: i1)].value) - zeroUnicode
            while i2 >= 0 {
                let item2 = Int(unicodeScalars2[unicodeScalars2.index(unicodeScalars2.startIndex, offsetBy: i2)].value) - zeroUnicode
                sumArray[(i1 + i2 + 1)] += item1 * item2

                i2 -= 1
            }

            i1 -= 1
        }

        var i3 = l - 1
        while i3 >= 0 {
            if sumArray[i3] > 9 {
                sumArray[i3 - 1] += sumArray[i3] / 10
                sumArray[i3] = sumArray[i3] % 10
            }

            i3 -= 1
        }

        var i4 = 0
        while sumArray[i4] == 0 {
            i4 += 1
        }

        var result: String = ""
        while i4 < l {
            result.append(String(sumArray[i4]))
            i4 += 1
        }

        return result
    }
}
```


## 结语

如果你同我一样热爱数据结构、算法、LeetCode，可以关注我 GitHub 上的 LeetCode 题解：[awesome-swift-leetcode][zgpeace]



[title]: https://leetcode.com/problems/multiply-strings
[zgpeace]: https://github.com/zgpeace/awesome-swift-leetcode
