---
layout: post
title: 341.扁平化嵌套列表迭代器
categories:
  - LeetCode
tags:
  - stack
summary: 给定一个嵌套的整型列表。设计一个迭代器，使其能够遍历这个整型列表中的所有整数。
abbrlink: b4c84e9e
---

### 题目要求
给定一个嵌套的整型列表。设计一个迭代器，使其能够遍历这个整型列表中的所有整数。 
列表中的项或者为一个整数，或者是另一个列表。

### 题目示例
- **`示例 1:`** 
```
输入: [[1,1],2,[1,1]]
输出: [1,1,2,1,1]
解释: 通过重复调用 next 直到 hasNext 返回false，next 返回的元素的顺序应该是: [1,1,2,1,1]。
```

- **`示例 2:`** 
```
输入: [1,[4,[6]]]
输出: [1,4,6]
解释: 通过重复调用 next 直到 hasNext 返回false，next 返回的元素的顺序应该是: [1,4,6]。
```


### 解题思路
利用递归，nestedList遍历到无嵌套数组时，直接添加进自定义一维数组中；遍历到嵌套数组时，进行递归调用

### 解题代码
```java
/**
 * // This is the interface that allows for creating nested lists.
 * // You should not implement it, or speculate about its implementation
 * public interface NestedInteger {
 *
 *     // @return true if this NestedInteger holds a single integer, rather than a nested list.
 *     public boolean isInteger();
 *
 *     // @return the single integer that this NestedInteger holds, if it holds a single integer
 *     // Return null if this NestedInteger holds a nested list
 *     public Integer getInteger();
 *
 *     // @return the nested list that this NestedInteger holds, if it holds a nested list
 *     // Return null if this NestedInteger holds a single integer
 *     public List<NestedInteger> getList();
 * }
 */
public class NestedIterator implements Iterator<Integer> {

    private List<Integer> list = new ArrayList<>();
    private int pointer = 0;

    public NestedIterator(List<NestedInteger> nestedList) {
        resolve(nestedList);
    }

    public void resolve(List<NestedInteger> nestedList) {
        for (int i = 0 ; i < nestedList.size() ; i++) {
            NestedInteger t = nestedList.get(i);
            if (t.isInteger()) {
                list.add(t.getInteger());
            } else {
                resolve(t.getList());
            }
        }
    }

    @Override
    public Integer next() {
        return list.get(pointer++);
    }

    @Override
    public boolean hasNext() {
        return pointer < list.size();
    }
}

/**
 * Your NestedIterator object will be instantiated and called as such:
 * NestedIterator i = new NestedIterator(nestedList);
 * while (i.hasNext()) v[f()] = i.next();
 */
```

### 题目来源
LeetCode-[341.扁平化嵌套列表迭代器](https://leetcode-cn.com/problems/flatten-nested-list-iterator/)