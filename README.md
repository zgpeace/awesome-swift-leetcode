# awesome-swift-leetcode
leetcode swift 版本 4.2

awesome-swfit 是用swift实现另一位java实现的LeetCode算法[awesome-java-leetcode](https://raw.githubusercontent.com/Blankj/awesome-java-leetcode)

```
1,10,13,15,17,20,23,25,26,28,33,38,43,44,49,50,56,57,67,68,69,71,75,76
78,79,80,85,88,90,91,98,102,117,121,125,127,128,133,139,146,157,158,161
168,173,200,206,208,209,210,211,215,218,221,234,235,236,238,252,253,257
261,265,269,273,274,275,277,278,282,283,285,286,297,301,311,314,325,334
341,377,380,398,404,410,461,477,494,523,525,534,535,543,554
```

如果想知道更多公司 LeetCode 面试题，可以参看 [Companies.md][companies]。

附上镇楼诗：

> 明有科举八股，今有 LeetCode。  
> 八股定格式而取文采心意，LeetCode 定题目且重答案背诵。  
> 美其名曰："practice makes perfect."  
> 为何今不如古？  
> 非也非也，  
> 科举为国取士，LeetCode 为 Google 筛码工，各取所需也。  


## Easy

| #    | Title                                    | Tag                                      |
| :--- | :--------------------------------------- | :--------------------------------------- |
| 1    | [Two Sum][001]                           | Array, Hash Table                        |
| 7    | [Reverse Integer][007]                   | Math                                     |
| 9    | [Palindrome Number][009]                 | Math                                     |
| 13   | [Roman to Integer][013]                  | Math, String                             |
| 14   | [Longest Common Prefix][014]             | String                                   |
| 20   | [Valid Parentheses][020]                 | Stack, String                            |
| 21   | [Merge Two Sorted Lists][021]            | Linked List                              |
| 26   | [Remove Duplicates from Sorted Array][026] | Array, Two Pointers                      |
| 27   | [Remove Element][027]                    | Array, Two Pointers                      |
| 28   | [Implement strStr()][028]                | Two Pointers, String                     |
| 35   | [Search Insert Position][035]            | String                                   |
| 38   | [Count and Say][038]                     | String                                   |
| 53   | [Maximum Subarray][053]                  | Array, Divide and Conquer, Dynamic Programming |
| 58   | [Length of Last Word][058]               | String                                   |
| 66   | [Plus One][066]                          | Array, Math                              |
| 67   | [Add Binary][067]                        | Math, String                             |
| 69   | [Sqrt(x)][069]                           | Binary Search, Math                      |
| 70   | [Climbing Stairs][070]                   | Dynamic Programming                      |
| 83   | [Remove Duplicates from Sorted List][083] | Linked List                              |
| 88   | [Merge Sorted Array][088]                | Array, Two Pointers                      |
| 100  | [Same Tree][100]                         | Tree, Depth-first Search                 |
| 101  | [Symmetric Tree][101]                    | Tree, Depth-first Search, Breadth-first Search |
| 104  | [Maximum Depth of Binary Tree][104]      | Tree, Depth-first Search                 |
| 107  | [Binary Tree Level Order Traversal II][107] | Tree, Breadth-first Search               |
| 108  | [Convert Sorted Array to Binary Search Tree][108] | Tree, Depth-first Search                 |
| 110  | [Balanced Binary Tree][110]              | Tree, Depth-first Search                 |
| 111  | [Minimum Depth of Binary Tree][111]      | Tree, Depth-first Search, Breadth-first Search |
| 112  | [Path Sum][112]                          | Tree, Depth-first Search                 |
| 118  | [Pascal's Triangle][118]                 | Array                                    |
| 119  | [Pascal's Triangle II][119]              | Array                                    |
| 121  | [Best Time to Buy and Sell Stock][121]   | Array, Dynamic Programmin                |
| 122  | [Best Time to Buy and Sell Stock II][122] | Array, Greedy                            |
| 543  | [Diameter of Binary Tree][543]           | Tree                                     |


## Medium

| #    | Title                                    | Tag                              |
| :--- | :--------------------------------------- | :------------------------------- |
| 2    | [Add Two Numbers][002]                   | Linked List, Math                |
| 3    | [Longest Substring Without Repeating Characters][003] | Hash Table, Two Pointers, String |
| 5    | [Longest Palindromic Substring][005]     | String, Dynamic Programming      |
| 6    | [ZigZag Conversion][006]                 | String                           |
| 8    | [String to Integer (atoi)][008]          | Math, String                     |
| 11   | [Container With Most Water][011]         | Array, Two Pointers              |
| 12   | [Integer to Roman][012]                  | Math, String                     |
| 15   | [3Sum][015]                              | Array, Two Pointers              |
| 15   | [3Sum Closest][016]                      | Array, Two Pointers              |
| 17   | [Letter Combinations of a Phone Number][017] | String, Backtracking             |
| 18   | [4Sum][018]                              | Array, Hash Table, Two Pointers  |
| 19   | [Remove Nth Node From End of List][019]  | Linked List, Two Pointers        |
| 22   | [Generate Parentheses][022]              | String, Backtracking             |
| 24   | [Swap Nodes in Pairs][024]               | Linked List                      |
| 29   | [Divide Two Integers][029]               | Math, Binary Search              |
| 33   | [Search in Rotated Sorted Array][033]    | Arrays, Binary Search            |
| 43   | [Multiply Strings][043]                  | Math, String                     |
| 49   | [Group Anagrams][049]                    | Hash Table, String               |
| 50   | [Pow(x, n)][050]                         | Math, Binary Search              |
| 56   | [Merge Intervals][056]                   | Array, Sort                      |
| 554  | [Brick Wall][554]                        | Hash Table                       |


## Hard

| #    | Title                                    | Tag                                      |
| :--- | :--------------------------------------- | :--------------------------------------- |
| 4    | [Median of Two Sorted Arrays][004]       | Array, Binary Search, Divide and Conquer |
| 10   | [Regular Expression Matching][010]       | String, Dynamic Programming, Backtracking |
| 23   | [Merge k Sorted Lists][023]              | Linked List, Divide and Conquer, Heap    |
| 25   | [Reverse Nodes in k-Group][025]          | Linked List                              |
| 30   | [Substring with Concatenation of All Words][030] | Hash Table, Two Pointers, String         |
| 44   | [Wildcard Matching][044]                 | String, Dynamic Programming, Backtracking, Greedy |
| 57   | [Insert Interval][057]                   | Array, Sort                              |
| 68   | [Text Justification][068]                | String                                   |




[src]: https://github.com/Blankj/awesome-java-leetcode/tree/master/src
[note]: https://github.com/Blankj/awesome-java-leetcode/tree/master/note
[companies]: https://github.com/Blankj/awesome-java-leetcode/blob/master/Companies.md

[001]: https://github.com/zgpeace/awesome-swift-leetcode/blob/master/001TwoSum.md
[007]: https://github.com/zgpeace/awesome-swift-leetcode/blob/master/007ReverseInteger.md
[009]: https://github.com/zgpeace/awesome-swift-leetcode/blob/master/009isPalindromeNumber.md
[013]: https://github.com/zgpeace/awesome-swift-leetcode/blob/master/013RomanToInteger.md
