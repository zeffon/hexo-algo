---
layout: post
title: 222.完全二叉树的节点个数
categories:
  - LeetCode
tags:
  - binary Search Tree
summary: 给出一个完全二叉树，求出该树的节点个数。
abbrlink: 1f5935ac
---

### 题目要求
给出一个完全二叉树，求出该树的节点个数。

- **`说明:`**
完全二叉树的定义如下：在完全二叉树中，除了最底层节点可能没填满外，其余每层节点数都达到最大值，并且最下面一层的节点都集中在该层最左边的若干位置。若最底层为第 h 层，则该层包含 1~ 2h 个节点。


### 题目示例
- **`示例 1:`**
```
输入: 
    1
   / \
  2   3
 / \  /
4  5 6

输出: 6
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
    public int countNodes(TreeNode root) {
        if(root == null) {
            return 0;
        }
        return countNodes(root.left) + countNodes(root.right) + 1;
    }
}
```



### 题目来源
LeetCode-[222.完全二叉树的节点个数](https://leetcode-cn.com/problems/count-complete-tree-nodes/)
