# [Best Time to Buy and Sell Stock][title]

## Description

Say you have an array for which the *i*<sup>th</sup> element is the price of a given stock on day *i*.

If you were only permitted to complete at most one transaction (i.e., buy one and sell one share of the stock), design an algorithm to find the maximum profit.

Note that you cannot sell a stock before you buy one.

**Example 1:**

```
Input: [7,1,5,3,6,4]
Output: 5
Explanation: Buy on day 2 (price = 1) and sell on day 5 (price = 6), profit = 6-1 = 5.
             Not 7-1 = 6, as selling price needs to be larger than buying price.
```

**Example 2:**

```
Input: [7,6,4,3,1]
Output: 0
Explanation: In this case, no transaction is done, i.e. max profit = 0.
```

**Tags:** Array, Dynamic Programmin


## 思路

题意是给出一个数组代表每天的股票金额，让你在最多买卖一次的情况下算出最大的收益额，最简单的就是模拟即可，每次记录当前值减去最小值的差值，与上一次的进行比较然后更新最大值即可。

```swift
class Solution {
    func maxProfit(_ prices: [Int]) -> Int {
        var maxProfixInt = 0
        var minPriceInt = Int.max
        for item in prices {
            if minPriceInt > item {
                minPriceInt = item
            }
            let gap = item - minPriceInt
            if gap > maxProfixInt {
                maxProfixInt = gap
            }
        }

        return maxProfixInt
    }
}
```


## 结语

如果你同我一样热爱数据结构、算法、LeetCode，可以关注我 GitHub 上的 LeetCode 题解：[awesome-swift-leetcode][zgpeace]



[title]: https://leetcode.com/problems/best-time-to-buy-and-sell-stock
[zgpeace]: https://github.com/zgpeace/awesome-swift-leetcode
