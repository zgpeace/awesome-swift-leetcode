# [Best Time to Buy and Sell Stock II][title]

## Description

Say you have an array for which the *i*<sup>th</sup> element is the price of a given stock on day *i*.

Design an algorithm to find the maximum profit. You may complete as many transactions as you like (i.e., buy one and sell one share of the stock multiple times).

**Note:** You may not engage in multiple transactions at the same time (i.e., you must sell the stock before you buy again).

**Example 1:**

```
Input: [7,1,5,3,6,4]
Output: 7
Explanation: Buy on day 2 (price = 1) and sell on day 3 (price = 5), profit = 5-1 = 4.
             Then buy on day 4 (price = 3) and sell on day 5 (price = 6), profit = 6-3 = 3.
```

**Example 2:**

```
Input: [1,2,3,4,5]
Output: 4
Explanation: Buy on day 1 (price = 1) and sell on day 5 (price = 5), profit = 5-1 = 4.
             Note that you cannot buy on day 1, buy on day 2 and sell them later, as you are
             engaging multiple transactions at the same time. You must sell before buying again.
```

**Example 3:**

```
Input: [7,6,4,3,1]
Output: 0
Explanation: In this case, no transaction is done, i.e. max profit = 0.
```

**Tags:** Array, Greedy


## 思路

题意是给出一个数组代表每天的股票金额，在每天只能买或卖的情况下求出收益最高值，<br />
    这...，这也太简单了吧，把所有相邻递增的值都加起来即可。<br />
    实际上为greedy 贪婪算法，分析情况：<br />
    1、如果为一直递增，那么相当于最大的减去最小的，比如[1, 4, 5], (4 - 1) + (5 - 4) = 5 - 1;<br />
    2、如果有波峰，波谷，那么递增的则累加，比如[1, 4, 2, 8], (4 -1) + (8 - 2)<br />

```swift
class Solution {
    func maxProfit(_ prices: [Int]) -> Int {
        var maxProfitInt = 0
        if prices.count < 1 {
            return maxProfitInt
        }
        for i in 1..<prices.count {
            if prices[i] > prices[i - 1] {
                maxProfitInt += (prices[i] - prices[i - 1])
            }
        }

        return maxProfitInt
    }
}
```


## 结语

如果你同我一样热爱数据结构、算法、LeetCode，可以关注我 GitHub 上的 LeetCode 题解：[awesome-swift-leetcode][zgpeace]



[title]: https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii
[zgpeace]: https://github.com/zgpeace/awesome-swift-leetcode
