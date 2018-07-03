# [Remove Element][title]

## Description

Given an array *nums* and a value *val*, remove all instances of that value [**in-place**](https://en.wikipedia.org/wiki/In-place_algorithm) and return the new length.

Do not allocate extra space for another array, you must do this by **modifying the input array [in-place](https://en.wikipedia.org/wiki/In-place_algorithm) ** with O(1) extra memory.

The order of elements can be changed. It doesn't matter what you leave beyond the new length.

**Example 1:**

```
Given nums = [3,2,2,3], val = 3,

Your function should return length = 2, with the first two elements of nums being 2.

It doesn't matter what you leave beyond the returned length.
```

**Example 2:**

```
Given nums = [0,1,2,2,3,0,4,2], val = 2,

Your function should return length = 5, with the first five elements of nums containing 0, 1, 3, 0, and 4.

Note that the order of those five elements can be arbitrary.

It doesn't matter what values are set beyond the returned length.
```

**Clarification:**

Confused why the returned value is an integer but your answer is an array?

Note that the input array is passed in by **reference**, which means modification to the input array will be known to the caller as well.

Internally you can think of this:

```
// nums is passed in by reference. (i.e., without making a copy)
int len = removeElement(nums, val);

// any modification to nums in your function would be known by the caller.
// using the length returned by your function, it prints the first len elements.
for (int i = 0; i < len; i++) {
    print(nums[i]);
}
```

**Tags:** Array, Two Pointers


## 思路

题意是移除数组中值等于 `val` 的元素，并返回之后数组的长度，并且题目中指定空间复杂度为 O(1)，我的思路是用 `tail` 标记尾部，遍历该数组时当索引元素不等于 `val` 时，`tail` 加一，尾部指向当前元素，最后返回 `tail` 即可。

```swift
func removeElement(_ nums: inout [Int], _ val: Int) -> Int {
    var last = 0
    for item in nums {
        if item != val {
            nums[last] = item
            last += 1
        }
    }
    return last
}
var input1 = [3,2,2,3]
let val1 = 3
print("input: \(input1); val: \(val1); result: \(removeElement(&input1, val1)) \n resultArray:\(input1)")
var input2 = [0,1,2,2,3,0,4,2]
let val2 = 2
print("input: \(input2); val: \(val2); result: \(removeElement(&input2, val2)) \n resultArray:\(input2)")
```


## 结语

如果你同我一样热爱数据结构、算法、LeetCode，可以关注我 GitHub 上的 LeetCode 题解：[awesome-swift-leetcode][zgpeace]



[title]: https://leetcode.com/problems/remove-element
[zgpeace]: https://github.com/zgpeace/awesome-swift-leetcode
