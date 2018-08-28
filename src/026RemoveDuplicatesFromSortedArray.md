# [Remove Duplicates from Sorted Array][title]

## Description

Given a sorted array *nums*, remove the duplicates [**in-place**](https://en.wikipedia.org/wiki/In-place_algorithm) such that each element appear only *once* and return the new length.

Do not allocate extra space for another array, you must do this by **modifying the input array [in-place](https://en.wikipedia.org/wiki/In-place_algorithm)** with O(1) extra memory.

**Example 1:**

```
Given nums = [1,1,2],

Your function should return length = 2, with the first two elements of nums being 1 and 2 respectively.

It doesn't matter what you leave beyond the returned length.
```

**Example 2:**

```
Given nums = [0,0,1,1,1,2,2,3,3,4],

Your function should return length = 5, with the first five elements of nums being modified to 0, 1, 2, 3, and 4 respectively.

It doesn't matter what values are set beyond the returned length.
```

**Clarification:**

Confused why the returned value is an integer but your answer is an array?

Note that the input array is passed in by **reference**, which means modification to the input array will be known to the caller as well.

Internally you can think of this:

```
// nums is passed in by reference. (i.e., without making a copy)
int len = removeDuplicates(nums);

// any modification to nums in your function would be known by the caller.
// using the length returned by your function, it prints the first len elements.
for (int i = 0; i < len; i++) {
    print(nums[i]);
}
```

**Tags:** Array, Two Pointers


## 思路

题意是让你从一个有序的数组中移除重复的元素，并返回之后数组的长度。我的思路是判断长度小于等于 1 的话直接返回原长度即可，否则的话遍历一遍数组，用一个 `tail` 变量指向尾部，如果后面的元素和前面的元素不同，就让 `tail` 变量加一，最后返回 `tail` 即可。

```swift
func removeDuplicates(_ nums: inout [Int]) -> Int {
    let len = nums.count
    if len <= 1 {
        return len
    }
    var last = 1
    for i in 1..<len {
        if nums[i] != nums[i - 1] {
            nums[last] = nums[i]
            last += 1
        }
    }
    
    return last
}

var input1 = [1,1,2]
print("input1: \(input1) ;result: \(removeDuplicates(&input1))")
var input2 = [0,0,1,1,1,2,2,3,3,4]
print("input2: \(input2) ;result: \(removeDuplicates(&input2))")
```


## 结语

如果你同我一样热爱数据结构、算法、LeetCode，可以关注我 GitHub 上的 LeetCode 题解：[awesome-swift-leetcode][zgpeace]



[title]: https://leetcode.com/problems/remove-duplicates-from-sorted-array
[zgpeace]: https://github.com/zgpeace/awesome-swift-leetcode
