---
layout: post
title: 92.反转链表 II
categories:
  - LeetCode
tags:
  - linked List
summary: 反转从位置 m 到 n 的链表。请使用一趟扫描完成反转。
abbrlink: 3c5ad999
---

### 题目要求
反转从位置 m 到 n 的链表。请使用一趟扫描完成反转。

**`说明:`**
1 ≤ m ≤ n ≤ 链表长度。

### 题目示例
**`示例 1:`**
```
输入: 1->2->3->4->5->NULL, m = 2, n = 4
输出: 1->4->3->2->5->NULL
```

### 解题思路


### 解题代码
```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
class Solution {
    public ListNode reverseBetween(ListNode head, int m, int n) {
        ListNode dummy = new ListNode(0);
        dummy.next = head;
        ListNode pre = dummy;
        for(int i = 1; i < m; i++){
            pre = pre.next;
        }
        head = pre.next;
        for(int i = m; i < n; i++){
            ListNode nex = head.next;
            head.next = nex.next;
            nex.next = pre.next;
            pre.next = nex;
        }
        return dummy.next;
    }
}
```


### 题目来源
LeetCode-[92.反转链表 II](https://leetcode-cn.com/problems/reverse-linked-list-ii/)
