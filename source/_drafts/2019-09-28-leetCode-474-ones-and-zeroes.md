---
layout: post
title: 474.一和零
categories:
  - LeetCode
tags:
  - DP
summary: "你的任务是使用给定的\_m 个\_0\_和 n 个\_1\_，找到能拼出存在于数组中的字符串的最大数量。每个\_0\_和\_1\_至多被使用一次。"
abbrlink: d7b9bbcf
---

### 题目要求
在计算机界中，我们总是追求用有限的资源获取最大的收益。

现在，假设你分别支配着 m 个 0 和 n 个 1。另外，还有一个仅包含 0 和 1 字符串的数组。

你的任务是使用给定的 m 个 0 和 n 个 1 ，找到能拼出存在于数组中的字符串的最大数量。每个 0 和 1 至多被使用一次。

- **`注意:`**
1. 给定 0 和 1 的数量都不会超过 100。
1. 给定字符串数组的长度不会超过 600。


### 题目示例
- **`示例 1:`**  
```
输入: Array = {"10", "0001", "111001", "1", "0"}, m = 5, n = 3
输出: 4

解释: 总共 4 个字符串可以通过 5 个 0 和 3 个 1 拼出，即 "10","0001","1","0" 。
```

- **`示例 2:`**  
```
输入: Array = {"10", "0", "1"}, m = 1, n = 1
输出: 2

解释: 你可以拼出 "10"，但之后就没有剩余数字了。更好的选择是拼出 "0" 和 "1" 。
```

### 解题思路



### 解题代码
```java
class Solution {
    public int findMaxForm(String[] strs, int m, int n) {
        
    }
}
```

### 题目来源
LeetCode-[474.一和零](https://leetcode-cn.com/problems/ones-and-zeroes/)
