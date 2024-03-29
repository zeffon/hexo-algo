---
layout: post
title: 15.三数之和
categories:
  - LeetCode
tags:
  - lookup Table
summary: "给定一个包含 n 个整数的数组\_nums，判断\_nums\_中是否存在三个元素 a，b，c ，使得\_a + b + c = 0 ？找出所有满足条件且不重复的三元组。"
abbrlink: dc9aab9f
---

### 题目要求
给定一个包含 n 个整数的数组 nums，判断 nums 中是否存在三个元素 a，b，c ，使得 a + b + c = 0 ？找出所有满足条件且不重复的三元组。

**`注意`**：答案中不可以包含重复的三元组。



### 题目示例
**`示例:`** 
```
例如, 给定数组 nums = [-1, 0, 1, 2, -1, -4]，

满足要求的三元组集合为：
[
  [-1, 0, 1],
  [-1, -1, 2]
]
```

### 解题思路
1. 定义返回`数组res`，如果为null或者长度小于3则返回空
1. 先对数组nums`排序`，排序后，如果`最小值`大于0或者`最大值`小于0则不可能三个数加起来`等于0`，直接返回空
1. 遍历数组，中注意这里需要`当前i指针`、`l指针`(i + 1)、`r指针`(nums.length - 1)共三个指针。
1. 随着`i指针`的遍历，对l、r指针控制，找到三指针`之和`为0 nums[i] + nums[l] + nums[r] == 0，将它们添加进`数组res`中。随后对l，r指针进行`移动`，并判断移动后的`左右指针`是否重复，重复则`再移动`。


### 解题代码
```java
class Solution {
    public List<List<Integer>> threeSum(int[] nums) {

        List<List<Integer>> res = new ArrayList<>();
        if(nums == null || nums.length <= 2)
            return res;
        
        Arrays.sort(nums);
        if(nums[0] > 0 || nums[nums.length - 1] < 0)
            return res;

        for(int i = 0; i < nums.length - 2; i++) {
            // 当不是第一个元素的时候，如果该元素和前面的元素相等则continue；删除重复
            if(i != 0 && nums[i] == nums[i - 1]) {
                continue;
            }
                
            int l = i + 1;
            int r = nums.length - 1;
            // 左指针小于右指针，而且当前值必须小于1，否则三个数都大于等于1.
            while(l < r && nums[i] < 1) {
                int p = nums[i] + nums[l] + nums[r];
                if(p == 0) {
                    res.add(Arrays.asList(nums[i], nums[l], nums[r]));
                    l++;
                    r--;
                    // 检查左右指针是否重复，重复则移动
                    while(l < r && nums[l] == nums[l - 1]) {
                        l++;
                    }
                    while(l < r && nums[r] == nums[r + 1]) {
                        r--;
                    }
                } else if (p < 0) {
                    l++;
                } else {
                    r--;
                }
            }
        }
        return res;
    }    
}
```

### 题目来源
LeetCode-[15.三数之和](https://leetcode-cn.com/problems/3sum/)
