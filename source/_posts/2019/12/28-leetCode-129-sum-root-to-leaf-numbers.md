---
layout: post
title: 129.求根到叶子节点数字之和
categories:
  - LeetCode
tags:
  - binary Search Tree
abbrlink: ab15f1b5
---

### 题目要求
给定一个二叉树，它的每个结点都存放一个 0-9 的数字，每条从根到叶子节点的路径都代表一个数字。

例如，从根到叶子节点路径 1->2->3 代表数字 123。
计算从根到叶子节点生成的所有数字之和。
<!-- more -->
- **`说明:`**
叶子节点是指没有子节点的节点。

### 题目示例
- **`示例 1:`**
```
输入: [1,2,3]
    1
   / \
  2   3
输出: 25
解释:
从根到叶子节点路径 1->2 代表数字 12.
从根到叶子节点路径 1->3 代表数字 13.
因此，数字总和 = 12 + 13 = 25.
```

- **`示例 2:`**
```
输入: [4,9,0,5,1]
    4
   / \
  9   0
 / \
5   1
输出: 1026
解释:
从根到叶子节点路径 4->9->5 代表数字 495.
从根到叶子节点路径 4->9->1 代表数字 491.
从根到叶子节点路径 4->0 代表数字 40.
因此，数字总和 = 495 + 491 + 40 = 1026.
```


### 解题思路



### 解题代码
```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {
    private int sumNum = 0;
    public int sumNumbers(TreeNode root) {
        if(root == null) {
            return 0;
        }
        dfs(root, 0);
        return sumNum;
    }
    private void dfs(TreeNode root, int sum) {
        if(root.left == null && root.right == null) {
            sumNum += sum + root.val; 
        }
        if(root.left != null) {
            dfs(root.left, sum * 10 + root.val * 10);
        }
        if(root.right != null) {
            dfs(root.right, sum * 10 + root.val * 10);
        }
    }
}
```



### 题目来源
LeetCode-[129.求根到叶子节点数字之和](https://leetcode-cn.com/problems/sum-root-to-leaf-numbers/)
