---
layout: post
title: 404.左叶子之和
categories:
  - LeetCode
tags:
  - binary Search Tree
summary: 计算给定二叉树的所有左叶子之和。
abbrlink: 724fee56
---

### 题目要求
计算给定二叉树的所有左叶子之和。


### 题目示例
- **`示例:`**
```
    3
   / \
  9  20
    /  \
   15   7

在这个二叉树中，有两个左叶子，分别是 9 和 15，所以返回 24
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
    public int sumOfLeftLeaves(TreeNode root) {
        if(root == null) {
            return 0;
        }
        return dfs(root, false);
    }

    public int dfs(TreeNode node, boolean isLeft) {
        if(node.left == null && node.right == null) {
            if(isLeft) {
                return node.val;
            }
            return 0;
        }
        int res = 0;
        if(node.left != null) {
            res += dfs(node.left, true);
        }
        if(node.right != null) {
            res += dfs(node.right, false);
        }
        return res;
    }
}
```



### 题目来源
LeetCode-[404.左叶子之和](https://leetcode-cn.com/problems/sum-of-left-leaves/)
