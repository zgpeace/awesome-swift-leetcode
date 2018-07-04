# [Maximum Subarray][title]

## Description

Given an integer array `nums`, find the contiguous subarray (containing at least one number) which has the largest sum and return its sum.

**Example:**

```
Input: [-2,1,-3,4,-1,2,1,-5,4],
Output: 6
Explanation: [4,-1,2,1] has the largest sum = 6.
```

**Follow up:**

If you have figured out the O(*n*) solution, try coding another solution using the divide and conquer approach, which is more subtle.

**Tags:** Array, Divide and Conquer, Dynamic Programming


## 思路 0

题意是求数组中子数组的最大和，这种最优问题一般第一时间想到的就是动态规划，我们可以这样想，当部分序列和大于零的话就一直加下一个元素即可，并和当前最大值进行比较，如果出现部分序列小于零的情况，那肯定就是从当前元素算起。其转移方程就是 `dp[i] = nums[i] + (dp[i - 1] > 0 ? dp[i - 1] : 0);`，由于我们不需要保留 dp 状态，故可以优化空间复杂度为 1，即 `dp = nums[i] + (dp > 0 ? dp : 0);`。

```swift
func maxSubArray(_ nums: [Int]) -> Int {
    var maxSum = nums[0]
    var lastSum = maxSum
    var indexBegin = 0
    var indexEnd = 0
    for (index, value) in nums.enumerated() {
        if index == 0 {
            continue
        }
        if lastSum <= 0 {
            indexBegin = index
        }
        lastSum = value + (lastSum > 0 ? lastSum : 0)
        if lastSum > maxSum {
            maxSum = lastSum
            indexEnd = index
        }
    }
    print("maxSubArray")
    for index in indexBegin...indexEnd {
        print("\(nums[index])")
    }
    
    return maxSum
}

let input = [-2,1,-3,4,-1,2,1,-5,4]
print("input: \(input); maxSum: \(maxSubArray(input))")
```

## 思路 1

题目也给了我们另一种思路，就是分治，所谓分治就是把问题分割成更小的，最后再合并即可，我们把 `nums` 一分为二先，那么就有两种情况，一种最大序列包括中间的值，一种就是不包括，也就是在左边或者右边；当最大序列在中间的时候那我们就把它两侧的最大和算出即可；当在两侧的话就继续分治即可。

```swift
func maxSubArrayWithDivideConquer(_ nums: [Int]) -> Int {
    return devideHelper(nums, 0, nums.count - 1)
}

func devideHelper(_ nums: [Int], _ left: Int, _ right: Int) -> Int {
    if left >= right {
        return nums[left]
    }
    let mid = (left + right) >> 1
    let maxLeftDevideSum = devideHelper(nums, left, mid)
    let maxRightDevideSum = devideHelper(nums, mid + 1, right)
    var maxLeftSum = nums[mid]
    var maxRightSum = nums[mid + 1]
    var temp = 0
    var tempLeftIndex = mid
    while tempLeftIndex > left {
        temp += nums[tempLeftIndex]
        if temp > maxLeftSum {
            maxLeftSum = temp
        }
        
        tempLeftIndex -= 1
    }
    
    temp = 0
    for i in (mid + 1)...right {
        temp += nums[i]
        if temp > maxRightSum {
            maxRightSum = temp
        }
    }
    
    return max(max(maxLeftDevideSum, maxRightDevideSum), maxLeftSum + maxRightSum)
}


let input = [-2,1,-3,4,-1,2,1,-5,4]
//print("input: \(input); maxSum: \(maxSubArray(input))")
print("input: \(input); maxSum: \(maxSubArrayWithDivideConquer(input))")
```


## 结语

如果你同我一样热爱数据结构、算法、LeetCode，可以关注我 GitHub 上的 LeetCode 题解：[awesome-swift-leetcode][zgpeace]



[title]: https://leetcode.com/problems/maximum-subarray
[zgpeace]: https://github.com/zgpeace/awesome-swift-leetcode
