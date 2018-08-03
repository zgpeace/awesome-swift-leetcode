# [4Sum][title]

## Description

Given an array `nums` of *n* integers and an integer `target`, are there elements *a*, *b*, *c*, and *d* in `nums` such that *a* + *b* + *c* + *d* = `target`? Find all unique quadruplets in the array which gives the sum of `target`.

**Note:**

The solution set must not contain duplicate quadruplets.

**Example:**

```
Given array nums = [1, 0, -1, 0, -2, 2], and target = 0.

A solution set is:
[
  [-1,  0, 0, 1],
  [-2, -1, 1, 2],
  [-2,  0, 0, 2]
]
```

**Tags:** Array, Hash Table, Two Pointers


## 思路 0

题意是让你从数组中找出所有四个数的和为 `target` 的元素构成的非重复序列，该题和 [3Sum][015] 的思路基本一样，先对数组进行排序，然后遍历这个排序数组，因为这次是四个元素的和，所以外层需要两重循环，然后还是用两个指针分别指向当前元素的下一个和数组尾部，判断四者的和与 `target` 的大小来移动两个指针，其中细节操作还是优化和去重。

```swift
class Solution {
    func fourSum(_ nums: [Int], _ target: Int) -> [[Int]] {
        //method 1: queue
        var resultList: [[Int]] = [[Int]]()
        let len = nums.count
        if len < 4 {
            return resultList
        }
        var numsList = nums
        numsList.sort()
        let max = numsList[len - 1]
        if max * 4 < target {
            return resultList
        }
        let firstMaxIndex = len - 3
        var i = 0
        while i < firstMaxIndex {
            //the small is too big, then break
            if numsList[i] * 4 > target {
                break
            }
            //the small is too small, then i++, continue
            if numsList[i] + max * 3 < target {
                repeat {
                    i += 1
                } while (numsList[i - 1] == numsList[i] && i < firstMaxIndex)
                continue
            }

            let secondMaxIndex = len - 2
            var j = i + 1
            while j < secondMaxIndex {
                let subSum = numsList[i] + numsList[j]
                //the small is too big, then break
                if subSum + numsList[j] * 2 > target {
                    break
                }
                //the small is too small, then j++, continue
                if subSum + max * 2 < target {
                    repeat {
                        j += 1
                    } while (numsList[j - 1] == numsList[j] && j < secondMaxIndex)
                    continue
                }

                var left = j + 1
                var right = len - 1
                while left < right {
                    //the small is too big, then break
                    if subSum + numsList[left] * 2 > target {
                        break
                    }
                    let sum = subSum + numsList[left] + numsList[right]

                    if sum == target {
                        resultList.append([numsList[i], numsList[j], numsList[left], numsList[right]])

                        repeat {
                            left += 1
                        } while (numsList[left - 1] == numsList[left] && left < right)

                        repeat {
                            right -= 1
                        } while (numsList[right + 1] == numsList[right] && left < right)
                    } else if sum < target {
                        repeat {
                            left += 1
                        } while (numsList[left - 1] == numsList[left] && left < right)
                    } else {
                        repeat {
                            right -= 1
                        } while (numsList[right + 1] == numsList[right] && left < right)
                    }
                }

                repeat {
                    j += 1
                } while (numsList[j - 1] == numsList[j] && j < secondMaxIndex)
            }

            repeat {
                i += 1
            } while (numsList[i - 1] == numsList[i] && i < firstMaxIndex)
        }

        return resultList
    }
}
```


## 思路 1

从 [Two Sum][001]、[3Sum][015] 到现在的 4Sum，其实都是把高阶降为低阶，那么我们就可以写出 kSum 的函数来对其进行降阶处理，降到 2Sum 后那么我们就可以对其进行最后的判断了，代码如下所示，其也做了相应的优化和去重。

```swift
class Solution {
    func fourSum(_ nums: [Int], _ target: Int) -> [[Int]] {
        //method 2: recursive
        let len = nums.count
        var resultList: [[Int]] = [[Int]]()

        if len < 4 {
            return resultList
        }
        var numsSort = nums.sorted()
        let max = numsSort[len - 1]

        if max * 4 < target {
            return resultList
        }
        resultList = helpSum(numsSort, 0, 4, target)

        return resultList
    }
    
    func helpSum(_ nums: [Int], _ start: Int, _ capacity: Int, _ target: Int) -> [[Int]] {
        var resultList: [[Int]] = [[Int]]()
        let len = nums.count

        if capacity == 2 {
            var left = start
            var right = len - 1
            while left < right {
                //small is too big, then break
                if nums[left] * 2 > target {
                    break
                }
                let sum = nums[left] + nums[right]

                if sum == target {
                    resultList.append([nums[left], nums[right]])
                    repeat {
                        left += 1
                    } while (nums[left - 1] == nums[left] && left < right)
                    repeat {
                        right -= 1
                    } while (nums[right + 1] == nums[right] && left < right)
                } else if sum < target {
                    repeat {
                        left += 1
                    } while (nums[left - 1] == nums[left] && left < right)
                } else {
                    repeat {
                        right -= 1
                    } while (nums[right + 1] == nums[right] && left < right)
                }
            }
        } else {
            let max = nums[len - 1]
            let end = len - (capacity - 1)
            var i = start
            while i < end {
                //small is too big, then break
                if nums[i] * capacity > target {
                    break
                }

                //small is too small, then i++, continue
                if nums[i] + max * (capacity - 1) < target {
                    repeat {
                        i += 1
                    } while (nums[i - 1] == nums[i] && i < end)
                }
                let tempList: [[Int]] = helpSum(nums, i + 1, capacity - 1, target - nums[i])
                for var subList in tempList {
                    subList.insert(nums[i], at: 0)
                    resultList.append(subList)
                }

                repeat {
                    i += 1
                } while (nums[i - 1] == nums[i] && i < end)
            }
        }

        return resultList
    }
}
```



## 结语

如果你同我一样热爱数据结构、算法、LeetCode，可以关注我 GitHub 上的 LeetCode 题解：[awesome-swift-leetcode][zgpeace]



[001]: https://github.com/zgpeace/awesome-swift-leetcode/blob/master/001TwoSum.md
[015]: https://github.com/zgpeace/awesome-swift-leetcode/blob/master/015ThreeSum.md
[title]: https://leetcode.com/problems/4sum
[zgpeace]: https://github.com/zgpeace/awesome-swift-leetcode
