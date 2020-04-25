<!--
 * @Author: FBB
 * @Date: 2020-04-25 15:15:27
 * @LastEditors: FBB
 * @LastEditTime: 2020-04-25 15:16:38
 * @Description:
 -->

> 原文链接

[https://leetcode.com/problems/majority-element-ii/](https://leetcode.com/problems/majority-element-ii/)

> 题目内容

Given an integer array of size n, find all elements that appear more than ⌊ n/3 ⌋ times.

**Note:** The algorithm should run in linear time and in O(1) space.

**Example 1:**

```
Input: [3,2,3]
Output: [3]
```

**Example 2:**

```
Input: [1,1,1,3,3,2,2,2]
Output: [1,2]
```

> 解题思路

```js
/**
 * @param {number[]} nums
 * @return {number[]}
 */
var majorityElement = function (nums) {
  const map = {};
  const result = [];
  nums.forEach((_) => (map[_] ? map[_]++ : (map[_] = 1)));
  for (let n in map) {
    if (map[n] > nums.length / 3) result.push(Number(n));
  }
  return result;
};
```
