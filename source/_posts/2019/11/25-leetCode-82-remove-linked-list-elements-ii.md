---
layout: post
title: 82.删除排序链表中的重复元素 II
categories:
  - LeetCode
tags:
  - linked List
summary: 给定一个排序链表，删除所有含有重复数字的节点，只保留原始链表中 没有重复出现 的数字。
abbrlink: 746ae810
---

### 题目要求
给定一个排序链表，删除所有含有重复数字的节点，只保留原始链表中 没有重复出现 的数字。

### 题目示例
**`示例 1:`**
```
输入: 1->2->3->3->4->4->5
输出: 1->2->5
```

**`示例 2:`**
```
输入: 1->1->1->2->3
输出: 2->3
```

### 解题思路
```
    null -> 1 -> 2 -> 3 -> 3 -> 4 -> 4 -> 5
     |      |
    pre    cur
            p
```


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
    public ListNode deleteDuplicates(ListNode head) {
        ListNode dummyHead = new ListNode(0);
        dummyHead.next = head;
        ListNode pre = dummyHead;
        ListNode cur = pre.next;

        while(cur != null) {
            int num = 0;
            ListNode p = cur;
            while(p != null && p.val == cur.val) {
                num++;
                p = p.next;
            }
            // num大于等于2时才存在重复节点
            if(num > 1) {
                pre.next = p;
            } else {
                pre = cur;
            }
            cur = p;
        }
        return dummyHead.next;
    }
}
```

### 题目来源
LeetCode-[82.删除排序链表中的重复元素 II](https://leetcode-cn.com/problems/remove-duplicates-from-sorted-list-ii/)
