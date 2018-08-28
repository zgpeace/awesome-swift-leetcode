# [Insert Interval][title]

## Description

Given a set of *non-overlapping* intervals, insert a new interval into the intervals (merge if necessary).

You may assume that the intervals were initially sorted according to their start times.

**Example 1:**

```
Input: intervals = [[1,3],[6,9]], newInterval = [2,5]
Output: [[1,5],[6,9]]
```

**Example 2:**

```
Input: intervals = [[1,2],[3,5],[6,7],[8,10],[12,16]], newInterval = [4,8]
Output: [[1,2],[3,10],[12,16]]
Explanation: Because the new interval [4,8] overlaps with [3,5],[6,7],[8,10].
```

**Tags:** Array, Sort


## 思路

题意是给你一组有序区间，和一个待插入区间，让你待插入区间插入到前面的区间中，我们分三步走：

1. 首先把有序区间中小于待插入区间的部分加入到结果中；

2. 其次是插入待插入区间，如果有交集的话取两者交集的端点值；

3. 最后把有序区间中大于待插入区间的部分加入到结果中；

```swift
/**
 * Definition for an interval.
 * public class Interval {
 *   public var start: Int
 *   public var end: Int
 *   public init(_ start: Int, _ end: Int) {
 *     self.start = start
 *     self.end = end
 *   }
 * }
 */
class Solution {
    func insert(_ intervals: [Interval], _ newInterval: Interval) -> [Interval] {
        if intervals.isEmpty {
            return [newInterval];
        }
        var resultList: [Interval] = [Interval]()
        var vnewInterval = newInterval
        var i: Int = 0

        //less than
        while i < intervals.count {
            let item = intervals[i]
            if item.end < vnewInterval.start {
                resultList.append(item)
            } else {
                break
            }

            i += 1
        }

        //cross area
        while i < intervals.count {
            let item = intervals[i]
            if item.start <= vnewInterval.end {
                vnewInterval.start = min(item.start, vnewInterval.start)
                vnewInterval.end = max(item.end, vnewInterval.end)
            } else {
                break
            }

            i += 1
        }

        resultList.append(vnewInterval)

        //more than
        while i < intervals.count {
            resultList.append(intervals[i])
            i += 1
        }

        return resultList
    }
}
```


## 结语

如果你同我一样热爱数据结构、算法、LeetCode，可以关注我 GitHub 上的 LeetCode 题解：[awesome-swift-leetcode][zgpeace]



[title]: https://leetcode.com/problems/insert-interval
[zgpeace]: https://github.com/zgpeace/awesome-swift-leetcode
