<!--
 * @Author: FBB
 * @Date: 2020-04-14 22:12:12
 * @LastEditors: FBB
 * @LastEditTime: 2020-04-14 22:20:51
 * @Description:
 -->

> 原文链接

[https://leetcode.com/problems/contiguous-array/](https://leetcode.com/problems/contiguous-array/)

> 题目内容
> Given a binary array, find the maximum length of a contiguous subarray with equal number of 0 and 1.

**Example 1:**

```
Input: [0,1]
Output: 2
Explanation: [0, 1] is the longest contiguous subarray with equal number of 0 and 1.
```

**Example 2:**

```
Input: [0,1,0]
Output: 2
Explanation: [0, 1] (or [1, 0]) is a longest contiguous subarray with equal number of 0 and 1.
```

**Note:**The length of the given binary array will not exceed 50,000.

> 解题思路

- 思路 1
  如果当前元素是 0,则标记当前为-1，这样将查找 0 和 1 个数相同的子序列转换成查找和为 0 的子序列。利用 map 记录检测过的子序列的和 sum 和对应的起始坐标 i，若当前累加和已经出现过，意味着存在一段 0 和 1 相等的子序列，更新当前的最大值

```js
/**
 * @param {number[]} nums
 * @return {number}
 */
var findMaxLength = function (nums) {
  let hash = { 0: -1 };
  let count = 0;
  let max = 0;
  for (let i = 0; i < nums.length; i++) {
    nums[i] === 0 ? count-- : count++;
    hash[count] !== null
      ? (max = Math.max(max, i - hash[count]))
      : (hash[count] = i);
  }
  return max;
};
```
