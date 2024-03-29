---
layout: post
title: 150.逆波兰表达式求值
categories:
  - LeetCode
tags:
  - stack
summary: 根据逆波兰表示法，求表达式的值。
abbrlink: 8533a662
---

### 题目要求
根据逆波兰表示法，求表达式的值。  
有效的运算符包括 +, -, *, / 。每个运算对象可以是整数，也可以是另一个逆波兰表达式。  

- **`说明：`** 
1. 整数除法只保留整数部分。
1. 给定逆波兰表达式总是有效的。换句话说，表达式总会得出有效数值且不存在除数为 0 的情况。

### 题目示例
- **`示例 1:`** 
```
输入: ["2", "1", "+", "3", "*"]
输出: 9
解释: ((2 + 1) * 3) = 9
```

- **`示例 2:`** 
```
输入: ["4", "13", "5", "/", "+"]
输出: 6
解释: (4 + (13 / 5)) = 6
```

- **`示例 3:`** 
```
输入: ["10", "6", "9", "3", "+", "-11", "*", "/", "*", "17", "+", "5", "+"]
输出: 22
解释: 
  ((10 * (6 / ((9 + 3) * -11))) + 17) + 5
= ((10 * (6 / (12 * -11))) + 17) + 5
= ((10 * (6 / -132)) + 17) + 5
= ((10 * 0) + 17) + 5
= (0 + 17) + 5
= 17 + 5
= 22
```

### 解题思路



### 解题代码
```java
class Solution {
    public int evalRPN(String[] tokens) {
        Stack<Integer> stack = new Stack<>();
        for(String s : tokens) {
            if(s.equals("+") || s.equals("-") || s.equals("*") || s.equals("/")) {
                int a = stack.pop();
                int b = stack.pop();

                if(s.equals("+")) {
                    stack.push(b + a);
                }
                if(s.equals("-")) {
                    stack.push(b - a);
                }
                if(s.equals("*")) {
                    stack.push(b * a);
                }
                if(s.equals("/")) {
                    stack.push(b / a);
                }
            } else {
                stack.push(Integer.parseInt(s));
            }
        }
        return stack.peek();
    }
}
```

### 题目来源
LeetCode-[150.逆波兰表达式求值](https://leetcode-cn.com/problems/evaluate-reverse-polish-notation/)