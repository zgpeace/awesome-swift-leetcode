# awesome-swift-leetcode
leetcode swift 版本 4.2

算法解决题目为 LeetCode 上 Facebook 的面试题目:
```
1,10,13,15,17,20,23,25,26,28,33,38,43,44,49,50,56,57,67,68,69,71,75,76
78,79,80,85,88,90,91,98,102,117,121,125,127,128,133,139,146,157,158,161
168,173,200,206,208,209,210,211,215,218,221,234,235,236,238,252,253,257
261,265,269,273,274,275,277,278,282,283,285,286,297,301,311,314,325,334
341,377,380,398,404,410,461,477,494,523,525,534,535,543,554
```
java 实现的代码： [awesome-java-leetcode](https://github.com/zgpeace/awesome-java-leetcode), 更新原有库一些没有实现的算法。  

如果想知道更多公司 LeetCode 面试题，可以参看 [Companies.md][companies]。

附上镇楼诗：

> 明有科举八股，今有 LeetCode。  
> 八股定格式而取文采心意，LeetCode 定题目且重答案背诵。  
> 美其名曰："practice makes perfect."  
> 为何今不如古？  
> 非也非也，  
> 科举为国取士，LeetCode 为 Google 筛码工，各取所需也。  

参考： [Blankj/awesome-java-leetcode](https://github.com/Blankj/awesome-java-leetcode)

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
| 16   | [3Sum Closest][016]                      | Array, Two Pointers              |
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

[001]: https://github.com/zgpeace/awesome-swift-leetcode/blob/master/src/001TwoSum.md
[007]: https://github.com/zgpeace/awesome-swift-leetcode/blob/master/src/007ReverseInteger.md
[009]: https://github.com/zgpeace/awesome-swift-leetcode/blob/master/src/009isPalindromeNumber.md
[013]: https://github.com/zgpeace/awesome-swift-leetcode/blob/master/src/013RomanToInteger.md
[014]: https://github.com/zgpeace/awesome-swift-leetcode/blob/master/src/014LongestCommonPrefix.md
[020]: https://github.com/zgpeace/awesome-swift-leetcode/blob/master/src/020ValidParentheses.md
[021]: https://github.com/zgpeace/awesome-swift-leetcode/blob/master/src/021MergeTwoSortedLists.md
[026]: https://github.com/zgpeace/awesome-swift-leetcode/blob/master/src/026RemoveDuplicatesFromSortedArray.md
[027]: https://github.com/zgpeace/awesome-swift-leetcode/blob/master/src/027RemoveElement.md
[028]: https://github.com/zgpeace/awesome-swift-leetcode/blob/master/src/028ImplementStrStr.md
[035]: https://github.com/zgpeace/awesome-swift-leetcode/blob/master/src/035SearchInsertPostion
[038]: https://github.com/zgpeace/awesome-swift-leetcode/blob/master/src/038CountAndSay.md
[053]: https://github.com/zgpeace/awesome-swift-leetcode/blob/master/src/053MaximumSubarray.md
[058]: https://github.com/zgpeace/awesome-swift-leetcode/blob/master/src/058LengthOfLastWord.md
[066]: https://github.com/zgpeace/awesome-swift-leetcode/blob/master/src/066PlusOne.md
[067]: https://github.com/zgpeace/awesome-swift-leetcode/blob/master/src/067AddBinary.md
[069]: https://github.com/zgpeace/awesome-swift-leetcode/blob/master/src/069Sqrt.md
[070]: https://github.com/zgpeace/awesome-swift-leetcode/blob/master/src/070ClimbingStairs.md
[083]: https://github.com/zgpeace/awesome-swift-leetcode/blob/master/src/083RemoveDuplicatesFromSortedList.md
[088]: https://github.com/zgpeace/awesome-swift-leetcode/blob/master/src/088MergeSortedArray.md
[100]: https://github.com/zgpeace/awesome-swift-leetcode/blob/master/src/100SameTree.md
[101]: https://github.com/zgpeace/awesome-swift-leetcode/blob/master/src/101SymmetricTree.md
[104]: https://github.com/zgpeace/awesome-swift-leetcode/blob/master/src/104MaximumDepthOfBinaryTree.md
[107]: https://github.com/zgpeace/awesome-swift-leetcode/blob/master/src/107BinaryTreeLevelOrderTraversalII.md
[108]: https://github.com/zgpeace/awesome-swift-leetcode/blob/master/src/108ConvertSortedArrayToBinarySearchTree.md
[110]: https://github.com/zgpeace/awesome-swift-leetcode/blob/master/src/110BalancedBinaryTree.md
[111]: https://github.com/zgpeace/awesome-swift-leetcode/blob/master/src/111MinimumDepthOfBinaryTree.md
[112]: https://github.com/zgpeace/awesome-swift-leetcode/blob/master/src/112PathSum.md
[118]: https://github.com/zgpeace/awesome-swift-leetcode/blob/master/src/118PascalTriangle.md
[119]: https://github.com/zgpeace/awesome-swift-leetcode/blob/master/src/119PascalTriangleII.md
[121]: https://github.com/zgpeace/awesome-swift-leetcode/blob/master/src/121BestTimeToBuyAndSellStock.md
[122]: https://github.com/zgpeace/awesome-swift-leetcode/blob/master/src/122BestTimeToBuyAndSellStockII.md
[543]: https://github.com/zgpeace/awesome-swift-leetcode/blob/master/src/543DiameterOfBinaryTree.md
[002]: https://github.com/zgpeace/awesome-swift-leetcode/blob/master/src/002AddTwoNumbers.md
[003]: https://github.com/zgpeace/awesome-swift-leetcode/blob/master/src/003LongestSubstringWithoutRepeatingCharacters.md
[005]: https://github.com/zgpeace/awesome-swift-leetcode/blob/master/src/005LongestPalindromicSubstring.md
[006]: https://github.com/zgpeace/awesome-swift-leetcode/blob/master/src/006ZigzagConversion.md
[008]: https://github.com/zgpeace/awesome-swift-leetcode/blob/master/src/008StringToIntegerAtoi.md
[011]: https://github.com/zgpeace/awesome-swift-leetcode/blob/master/src/011ContainerWithMostWater.md
[012]: https://github.com/zgpeace/awesome-swift-leetcode/blob/master/src/012IntegerToRoman.md
[015]: https://github.com/zgpeace/awesome-swift-leetcode/blob/master/src/015ThreeSum.md
[016]: https://github.com/zgpeace/awesome-swift-leetcode/blob/master/src/016ThreeSumClosest.md
[017]: https://github.com/zgpeace/awesome-swift-leetcode/blob/master/src/017LetterCombinationsOfAPhoneNumber.md
[018]: https://github.com/zgpeace/awesome-swift-leetcode/blob/master/src/018FourSum.md
[019]: https://github.com/zgpeace/awesome-swift-leetcode/blob/master/src/019RemoveNthNodeFromEndOfList.md
[022]: https://github.com/zgpeace/awesome-swift-leetcode/blob/master/src/022GenerateParentheses.md
[024]: https://github.com/zgpeace/awesome-swift-leetcode/blob/master/src/024SwapNodesInPairs.md
[029]: https://github.com/zgpeace/awesome-swift-leetcode/blob/master/src/029DivideTwoIntegers.md
[033]: https://github.com/zgpeace/awesome-swift-leetcode/blob/master/src/033SearchInRotatedSortedArray.md
[043]: https://github.com/zgpeace/awesome-swift-leetcode/blob/master/src/043MultiplyStrings.md
[049]: https://github.com/zgpeace/awesome-swift-leetcode/blob/master/src/049GroupAnagrams.md
[050]: https://github.com/zgpeace/awesome-swift-leetcode/blob/master/src/050Pow.md
[056]: https://github.com/zgpeace/awesome-swift-leetcode/blob/master/src/056MergeIntervals.md
[554]: https://github.com/zgpeace/awesome-swift-leetcode/blob/master/src/554BrickWall.md

[004]: https://github.com/zgpeace/awesome-swift-leetcode/blob/master/src/004MedianOfTwoSotedArrays.md
[010]: https://github.com/zgpeace/awesome-swift-leetcode/blob/master/src/010RegularExpressionMatching.md
[023]: https://github.com/zgpeace/awesome-swift-leetcode/blob/master/src/023MergeKSortedLists.md
[025]: https://github.com/zgpeace/awesome-swift-leetcode/blob/master/src/025ReverseNodesInKGroup.md
[030]: https://github.com/zgpeace/awesome-swift-leetcode/blob/master/src/030SubstringWithConcatenationOfAllWords.md
[044]: https://github.com/zgpeace/awesome-swift-leetcode/blob/master/src/044WildcardMatching.md
[057]: https://github.com/zgpeace/awesome-swift-leetcode/blob/master/src/057InsertInterval.md
[068]: https://github.com/zgpeace/awesome-swift-leetcode/blob/master/src/068TestJustification.md
