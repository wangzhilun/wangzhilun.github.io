---
title: 每日一道leetcode 两数之和d
date: 2019-09-27 19:06:01
categories:
  - algorithm
  - leetcode
tags:
  - algorithm
  - hashmap
---
### 两数之和
> 题目见[两数之和](https://leetcode-cn.com/problems/two-sum/)

最暴力的方法是两次for循环遍历,时间复杂度是O(n^2)
优化点在于怎么快速查询出来值。
采用hashMap的方式,key是hash存储,能够快速搜索到key
```java
public class TowSum {

    public int[] twoSum(int[] nums, int target) {
        Map<Integer, Integer> map = new HashMap<>();
        for (int i = 0; i < nums.length; i++) {
            int j = target - nums[i];
            if (map.containsKey(j)) {
                return new int[]{map.get(j), i};
            }
            map.put(nums[i], i);
        }
        return null;
    }
}

```

附录:
- [hashmap源码分析](https://laoshirenclub.com/categories/java/hashmap/)
