---
layout: post
title: 130.被围绕的区域
categories:
  - LeetCode
tags:
  - recursion
summary: 给定一个 m x n 的非负整数矩阵来表示一片大陆上各个单元格的高度。
abbrlink: e759f1b
---

### 题目要求
给定一个 m x n 的非负整数矩阵来表示一片大陆上各个单元格的高度。“太平洋”处于大陆的左边界和上边界，而“大西洋”处于大陆的右边界和下边界。

规定水流只能按照上、下、左、右四个方向流动，且只能从高到低或者在同等高度上流动。

请找出那些水流既可以流动到“太平洋”，又能流动到“大西洋”的陆地单元的坐标。


- **`提示:`**
1. 输出坐标的顺序不重要
1. m 和 n 都小于150

### 题目示例
- **`示例:`**
```
给定下面的 5x5 矩阵:

  太平洋 ~   ~   ~   ~   ~ 
       ~  1   2   2   3  (5) *
       ~  3   2   3  (4) (4) *
       ~  2   4  (5)  3   1  *
       ~ (6) (7)  1   4   5  *
       ~ (5)  1   1   2   4  *
          *   *   *   *   * 大西洋

返回:

[[0, 4], [1, 3], [1, 4], [2, 2], [3, 0], [3, 1], [4, 0]] (上图中带括号的单元).
```

### 解题思路



### 解题代码
```java
class Solution {
    public void solve(char[][] board) {
        
    }
}
```



### 题目来源
LeetCode-[130.被围绕的区域](https://leetcode-cn.com/problems/surrounded-regions/)
