# [Median of Two Sorted Arrays][title]

## Description

There are two sorted arrays **nums1** and **nums2** of size m and n respectively.

Find the median of the two sorted arrays. The overall run time complexity should be O(log (m+n)).

**Example 1:**

```
nums1 = [1, 3]
nums2 = [2]

The median is 2.0
```

**Example 2:**

```
nums1 = [1, 2]
nums2 = [3, 4]

The median is (2 + 3)/2 = 2.5
```

**Tags:** Array, Binary Search, Divide and Conquer


## 思路

题意是给你两个已排序的递增数组，让你找出其中位数。

乍一看这题并不是很难，因为两序列有序，所以我们很容想到时间复杂度为 `O(m + n)` 的做法：依次取出两数组中较小的元素，然后找到中间的元素即可。但这题要求的时间复杂度为 `O(log(m + n))`，那么我们自然而然地就能想到二分查找法进行求解。

题目是让找两数组的中位数，我们可以泛化为求两数组中第 `k` 大的元素，那么，求中位数就是其中的一个特例而已。`helper` 函数所起到的作用就是求两数组中第 `k` 大的元素，下面来解释其原理：

假设数组分别记为 `A`，`B`，当前需要搜索第 `k` 大的数，于是我们可以考虑从数组 `A` 中取出前 `m` 个元素，从数组 `B` 中取出前 `k - m` 个元素。由于数组 `A`，`B` 分别排序，则 `A[m - 1]` 大于从数组 `A` 中取出的其他所有元素，`B[k - m - 1]` 大于数组 `B` 中取出的其他所有元素。此时，尽管取出元素之间的相对大小关系不确定，但 `A[m - 1]` 与 `B[k - m - 1]` 的较大者一定是这 `k` 个元素中最大的。那么，较小的那个元素一定不是第 `k` 大的，这里留给读者自己想象。

为叙述方便，假设 `A[m - 1]` 是较小的那个元素，那么我们可以把 `A[0]`，`A[1]`...`A[m - 1]` 排除掉，并且更新 `k` 值为 `k - m`，也就是下一次就是从剩余的元素中寻找第 `k - m` 大的元素，这样，我们就完成了一次范围缩小，同理进行下一轮的操作。

那么什么时候停止操作呢？分两种情况：

1. 当某个数组的数都被取完了，那么直接返回另一个数组的后 `k` 个元素即可。

2. 当 `k = 1` 时，也就是只需再找一个数即可，也就是取两者当前较小的那个即可。

特别地，我们选取 `m = k / 2`，下面是我画的草图，希望能帮助大家理解。

![](https://raw.githubusercontent.com/Blankj/awesome-java-leetcode/master/note/004/my_draw.jpg)

借助上面的理论，你能写出相关代码了吗？

```swift
class Solution {
    func findMedianSortedArrays(_ nums1: [Int], _ nums2: [Int]) -> Double {
        let len: Int = nums1.count + nums2.count
        if len % 2 == 0 {
            return (helper(nums1, 0, nums2, 0, len / 2) + helper(nums1, 0, nums2, 0, len / 2 + 1)) / 2.0
        }
        return helper(nums1, 0, nums2, 0, len / 2 + 1)
    }

    func helper(_ nums1: [Int], _ index1: Int, _ nums2: [Int], _ index2: Int, _ k: Int) -> Double {
        if index1 >= nums1.count {
            return Double(nums2[index2 + k - 1])
        }
        if index2 >= nums2.count {
            return Double(nums1[index1 + k - 1])
        }
        if k == 1 {
            return Double(min(nums1[index1], nums2[index2]))
        }
        let offset: Int = k / 2
        let position1: Int = index1 + offset - 1
        let position2: Int = index2 + offset - 1
        let val1: Int = position1 < nums1.count ? nums1[position1] : Int.max
        let val2: Int = position2 < nums2.count ? nums2[position2] : Int.max
        if val1 < val2 {
            return helper(nums1, index1 + offset, nums2, index2, k - offset)
        }

        return helper(nums1, index1, nums2, index2 + offset, k - offset)
    }
}
```


## 结语

如果你同我一样热爱数据结构、算法、LeetCode，可以关注我 GitHub 上的 LeetCode 题解：[awesome-swift-leetcode][zgpeace]



[title]: https://leetcode.com/problems/median-of-two-sorted-arrays
[zgpeace]: https://github.com/zgpeace/awesome-swift-leetcode
