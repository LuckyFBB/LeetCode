<!--
 * @Author: FBB
 * @Date: 2020-04-24 20:51:49
 * @LastEditors: FBB
 * @LastEditTime: 2020-04-24 20:59:07
 * @Description:
 -->

> 原文链接

[https://leetcode.com/problems/subarray-sum-equals-k/](https://leetcode.com/problems/subarray-sum-equals-k/)

> 题目内容

Given an array of integers and an integer k, you need to find the total number of continuous subarrays whose sum equals to k.

**Example 1:**

```
Input:nums = [1,1,1], k = 2
Output: 2
```

**Note:**

```
1. The length of the array is in range [1, 20,000].
2. The range of numbers in the array is [-1000, 1000] and the range of the integer k is [-1e7, 1e7].
```

> 解题思路

- 思路 1
  使用 map 数据结构，累加 sum 值，然后查找 sum-k 是否存在于 map 中

```js
/**
 * @param {number[]} nums
 * @param {number} k
 * @return {number}
 */
var subarraySum = function (nums, k) {
  let map = new Map();
  let sum = 0;
  let count = 0;
  map.set(0, 1);
  for (let i = 0; i < nums.length; i++) {
    sum += nums[i];
    if (map.has(sum - k)) {
      count += map.get(sum - k);
    }
    map.has(sum) ? map.set(sum, map.get(sum) + 1) : map.set(sum, 1);
  }

  return count;
};
```
