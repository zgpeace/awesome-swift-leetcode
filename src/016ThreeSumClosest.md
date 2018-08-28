# [3Sum Closest][title]

## Description

Given an array `nums` of *n* integers and an integer `target`, find three integers in `nums` such that the sum is closest to `target`. Return the sum of the three integers. You may assume that each input would have exactly one solution.

**Example:**

```
Given array nums = [-1, 2, 1, -4], and target = 1.

The sum that is closest to the target is 2. (-1 + 2 + 1 = 2).
```

**Tags:** Array, Two Pointers


## 思路

题意是让你从数组中找出最接近 `target` 的三个数的和，该题和 [3Sum][015] 的思路基本一样，先对数组进行排序，然后遍历这个排序数组，用两个指针分别指向当前元素的下一个和数组尾部，判断三者的和与 `target` 的差值来移动两个指针，并更新其结果，当然，如果三者的和直接与 `target` 值相同，那么返回 `target` 结果即可。

```swift
class Solution {
    func threeSumClosest(_ nums: [Int], _ target: Int) -> Int {
        var gapMin = Int.max
        var closestTarget = 0
        var numsArray:[Int] = nums
        numsArray.sort()
        let len = numsArray.count
        for i in 0..<(len - 2) {
            var left = i + 1
            var right = len - 1
            while left < right {
                let sum = numsArray[i] + numsArray[left] + numsArray[right]
                let currentGap = abs(sum - target)
                if currentGap == 0 {
                    return target
                }
                if currentGap < gapMin {
                    gapMin = currentGap
                    closestTarget = sum
                }

                if sum < target {
                    left += 1
                } else {
                    right -= 1
                }
            }
        }

        return closestTarget
    }
}
```


## 结语

如果你同我一样热爱数据结构、算法、LeetCode，可以关注我 GitHub 上的 LeetCode 题解：[awesome-swift-leetcode][zgpeace]



[015]: https://github.com/zgpeace/awesome-swift-leetcode/blob/master/015ThreeSum.md
[title]: https://leetcode.com/problems/3sum-closest
[zgpeace]: https://github.com/zgpeace/awesome-swift-leetcode
