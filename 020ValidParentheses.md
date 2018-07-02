# [Valid Parentheses][title]

## Description

Given a string containing just the characters `'('`, `')'`, `'{'`, `'}'`, `'['` and `']'`, determine if the input string is valid.

An input string is valid if:

1. Open brackets must be closed by the same type of brackets.
2. Open brackets must be closed in the correct order.

Note that an empty string is also considered valid.

**Example 1:**

```
Input: "()"
Output: true
```

**Example 2:**

```
Input: "()[]{}"
Output: true
```

**Example 3:**

```
Input: "(]"
Output: false
```

**Example 4:**

```
Input: "([)]"
Output: false
```

**Example 5:**

```
Input: "{[]}"
Output: true
```

**Tags:** Stack, String


## 思路

题意是判断括号匹配是否正确，很明显，我们可以用栈来解决这个问题，当出现左括号的时候入栈，当遇到右括号时，判断栈顶的左括号是否何其匹配，不匹配的话直接返回 `false` 即可，最终判断是否空栈即可，这里我们可以用数组模拟栈的操作使其操作更快，有个细节注意下 `top =  1;`，从而省去了之后判空的操作和 `top - 1` 导致数组越界的错误。

```swift
func isValid(_ s: String) -> Bool {
    var stack:[Character] = ["E"]
    var top: Int = 1
    for charItem in s {
        if charItem == "(" || charItem == "[" || charItem == "{" {
            stack.append(charItem)
            top = top + 1
        } else {
            let latestChar = stack[top - 1]
            if charItem == ")" && latestChar != "(" {
                return false
            } else if  charItem == "]" && latestChar != "[" {
                return false
            }  else if  charItem == "}" && latestChar != "{" {
                return false
            }
            
            if charItem == ")" || charItem == "]" || charItem == "}" {
                stack.popLast()
                top = top - 1
            }
        }
    }
    
    return top == 1
}

let input1 = "()"
print("input: \(input1), result: \(isValid(input1))")
let input2 = "()[]{}"
print("input: \(input2), result: \(isValid(input2))")
let input3 = "(]"
print("input: \(input3), result: \(isValid(input3))")
let input4 = "([)]"
print("input: \(input4), result: \(isValid(input4))")
let input5 = "{[]}"
print("input: \(input5), result: \(isValid(input5))")
```


## 结语

如果你同我一样热爱数据结构、算法、LeetCode，可以关注我 GitHub 上的 LeetCode 题解：[awesome-swift-leetcode][zgpeace]



[title]: https://leetcode.com/problems/valid-parentheses
[zgpeace]: https://github.com/zgpeace/awesome-swift-leetcode
