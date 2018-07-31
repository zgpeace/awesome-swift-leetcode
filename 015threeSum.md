# [3Sum][title]

## Description

Given an array `nums` of *n* integers, are there elements *a*, *b*, *c* in `nums` such that *a* + *b* + *c* = 0? Find all unique triplets in the array which gives the sum of zero.

**Note:**

The solution set must not contain duplicate triplets.

**Example:**

```
Given array nums = [-1, 0, 1, 2, -1, -4],

A solution set is:
[
  [-1, 0, 1],
  [-1, -1, 2]
]
```

**Tags:** Array, Two Pointers


## 思路

题意是让你从数组中找出所有三个和为 0 的元素构成的非重复序列，这样的话我们可以把数组先做下排序，然后遍历这个排序数组，用两个指针分别指向当前元素的下一个和数组尾部，判断三者的和与 0 的大小来移动两个指针，其中细节操作就是优化和去重。

```swift
class Solution {
    func threeSum(_ nums: [Int]) -> [[Int]] {
        var resultList:[[Int]] = [[Int]]()
        var numsArray:[Int] = nums
        let len = numsArray.count
        if len < 3 {
            return resultList
        }
        numsArray.sort()
        if numsArray[len - 1] < 0 {
            return resultList
        }
        var i = 0
        while i < len - 2 {
            if numsArray[i] > 0 {
                break
            }
            //i too small, i + max * 2 < 0 ,then i increase
            if numsArray[i] + 2 * numsArray[len - 1] < 0 {
                repeat {
                    i += 1
                } while (numsArray[i - 1] == numsArray[i] && i < len - 2)

                continue
            }

            var left = i + 1
            var right = len - 1
            while left < right {
                if numsArray[i] + numsArray[left] + numsArray[right] == 0 {
                    resultList.append([numsArray[i], numsArray[left], numsArray[right]])
                    repeat {
                        left += 1
                    } while (numsArray[left - 1] == numsArray[left] && left < right)

                    repeat {
                        right -= 1
                    } while (numsArray[right + 1] == numsArray[right] && left < right)
                } else if numsArray[i] + numsArray[left] + numsArray[right] < 0 {
                    repeat {
                        left += 1
                    } while (numsArray[left - 1] == numsArray[left] && left < right)
                } else {
                    repeat {
                        right -= 1
                    } while (numsArray[right + 1] == numsArray[right] && left < right)
                }

                if numsArray[right] < 0 {
                    break
                }
            }

            repeat {
                i += 1
            } while (numsArray[i - 1] == numsArray[i] && i < len - 2)
        }

       return resultList
    }
}
```


## 结语

如果你同我一样热爱数据结构、算法、LeetCode，可以关注我 GitHub 上的 LeetCode 题解：[awesome-swift-leetcode][zgpeace]



[title]: https://leetcode.com/problems/3sum
[zgpeace]: https://github.com/zgpeace/awesome-swift-leetcode
