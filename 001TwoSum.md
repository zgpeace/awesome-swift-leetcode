# [Two Sum][title]

## Description

Given an array of integers, return **indices** of the two numbers such that they add up to a specific target.

You may assume that each input would have ***exactly*** one solution, and you may not use the same element twice.

**Example:**

```
Given nums = [2, 7, 11, 15], target = 9,

Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].
```

**Tags:** Array, Hash Table


## 思路 0

题意是让你从给定的数组中找到两个元素的和为指定值的两个索引，最容易的当然是循环两次，复杂度为 `O(n^2)`。

```swift
func twoSum(_ nums: [Int], _ target: Int) -> [Int] {
    let numsSize = nums.count
    
    for i in stride(from: 0, to: numsSize, by: 1) {
        let itemI = nums[i]
        
        for j in stride(from: (i + 1), to: numsSize, by: 1) {
            let itemJ = nums[j]
            if itemI + itemJ == target {
                return [i, j]
            }
        }
    }
    
    fatalError()
}
```

## 思路 1

利用 HashMap 作为存储，键为目标值减去当前元素值，索引为值，比如 `i = 0` 时，此时首先要判断 `nums[0] = 2` 是否在 map 中，如果不存在，那么插入键值对 `key = 9 - 2 = 7, value = 0`，之后当 `i = 1` 时，此时判断 `nums[1] = 7` 已存在于 map 中，那么取出该 `value = 0` 作为第一个返回值，当前 `i` 作为第二个返回值，具体代码如下所示。

```swift
func twoSum(_ nums: [Int], _ target: Int) -> [Int] {
    var index:Int = 0
    var dic:[Int: Int] = [:]
    for item in nums {
        if dic.contains(where: { $0.key == item}) {
            return [dic[item]!, index];
        }
        
        dic[(target - item)] = index
        index = index + 1
    }
    
    fatalError()
}
```


## 结语

如果你同我一样热爱数据结构、算法、LeetCode，可以关注我 GitHub 上的 LeetCode 题解：[awesome-swift-leetcode][zgpeace]



[title]: https://leetcode.com/problems/two-sum
[zgpeace]: https://github.com/zgpeace/awesome-swift-leetcode
