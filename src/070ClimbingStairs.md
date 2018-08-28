# [Climbing Stairs][title]

## Description

You are climbing a stair case. It takes *n* steps to reach to the top.

Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?

**Note:** Given *n* will be a positive integer.

**Example 1:**

```
Input: 2
Output: 2
Explanation: There are two ways to climb to the top.
1. 1 step + 1 step
2. 2 steps
```

**Example 2:**

```
Input: 3
Output: 3
Explanation: There are three ways to climb to the top.
1. 1 step + 1 step + 1 step
2. 1 step + 2 steps
3. 2 steps + 1 step
```

**Tags:** Dynamic Programming


## 思路

 题意是爬楼梯，每次你只能爬一步或者两步，问到顶层共有多少种方案。<br />
 我们假设到顶层共有 f(n) 种，那么 f(n) = f(n - 1) + f(n - 2) 肯定是成立的，<br />
 意思就是我们迈向顶层的最后一步是在倒数第一级台阶或者在倒数第二级台阶。 <br />
 数学归纳法证明： <br />
 初始化成立：  f(0) = 1(不用走也就是1步到位), f(1) = 1, f(2) = f(0) + f(1); <br />
 假设：  f(n) = f(n - 1) + f(n - 2)成立，<br />
 那么：  f(n + 1) = f(n - 1) + f(n - 2) + f(n - 1), 所以 f(n + 1) = f(n) + f(n - 1) 成立 <br />
 得证。 <br />
 也就是 c = a + b; a = b; b = c; 循环即可。 <br /><br />
 
 算法我对空间复杂度进行了优化，因为在迭代过程中只需要两个变量即可。 <br />
 简化以后 b = a + b; a = b - a; 跟上面的等式一样，省掉了c的空间
```swift
func climbStairs(_ n: Int) -> Int {
    var n = n - 1
    var a = 1
    var b = 1
    
    while n > 0 {
        b = b + a
        a = b - a
        n -= 1
    }
    
    return b
}

let n1 = 2
print("n: \(n1), climbStairs: \(climbStairs(n1))")
let n2 = 3
print("n: \(n2), climbStairs: \(climbStairs(n2))")
let n3 = 20
print("n: \(n3), climbStairs: \(climbStairs(n3))")
```


## 结语

如果你同我一样热爱数据结构、算法、LeetCode，可以关注我 GitHub 上的 LeetCode 题解：[awesome-swift-leetcode][zgpeace]



[title]: https://leetcode.com/problems/climbing-stairs
[zgpeace]: https://github.com/zgpeace/awesome-swift-leetcode
