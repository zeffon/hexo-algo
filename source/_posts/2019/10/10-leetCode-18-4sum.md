---
layout: post
title: 18.四数之和
categories:
  - LeetCode
tags:
  - lookup Table
summary: "给定一个包含\_n 个整数的数组\_nums\_和一个目标值\_target，判断\_nums\_中是否存在四个元素 a，b，c\_和 d\_，使得\_a + b + c + d\_的值与\_target\_相等？找出所有满足条件且不重复的四元组。"
abbrlink: cce02fa8
---

### 题目要求
给定一个包含 n 个整数的数组 nums 和一个目标值 target，判断 nums 中是否存在四个元素 a，b，c 和 d ，使得 a + b + c + d 的值与 target 相等？找出所有满足条件且不重复的四元组。

**`注意`**：答案中不可以包含重复的四元组。



### 题目示例
**`示例:`** 
```
给定数组 nums = [1, 0, -1, 0, -2, 2]，和 target = 0。

满足要求的四元组集合为：
[
  [-1,  0, 0, 1],
  [-2, -1, 1, 2],
  [-2,  0, 0, 2]
]
```

### 解题思路
```
    -2   -1    0    0    1    2
    |     |    |              |
    i     j    l              r
```

1. 定义返回`数组res`，如果为null或者长度小于3则返回空
1. 先对数组nums`排序`(从小到大)
1. 遍历数组，中注意这里需要`当前i指针`、`j指针`(i + 1)、`l指针`(j + 1)、`r指针`(nums.length - 1)共三个指针。
1. 随着`i指针`的遍历，再内部遍历`j指针`，对l、r指针控制，找到四指针`之和`等于target，将它们添加进`数组res`中。随后对l，r指针进行`移动`，并判断移动后的`左右指针`是否重复，重复则`再移动`。


### 解题代码
```java
class Solution {
    public List<List<Integer>> fourSum(int[] nums, int target) {
        
        List<List<Integer>> res = new ArrayList<>();
        if(nums == null || nums.length < 4)
            return res;
        
        Arrays.sort(nums);
        
        for(int i = 0; i < nums.length - 3; i++) {
            if(i > 0 && nums[i] == nums[i - 1])
                continue;
            for(int j = i + 1; j < nums.length - 2; j++) {
                if(j > i + 1 && nums[j] == nums[j - 1])
                    continue;
                int l = j + 1;
                int r = nums.length - 1;
                while(l < r) {
                    int sum = nums[i] + nums[j] + nums[l] + nums[r];
                    if(sum == target) {
                        res.add(Arrays.asList(nums[i], nums[j], nums[l], nums[r]));
                        l++;
                        r--;
                        while(l < r && nums[l] == nums[l - 1]) {
                            l++;
                        }
                        while(l < r && nums[r] == nums[r + 1]) {
                            r--;
                        }
                    } else if(sum < target) {
                        l++;
                    } else {
                        r--;
                    }
                }
            }
        }
        return res;
    }
}
```

### 题目来源
LeetCode-[18.四数之和](https://leetcode-cn.com/problems/4sum/)
