<!--
 * @Author: FBB
 * @Date: 2020-06-11 20:24:38
 * @LastEditors: FBB
 * @LastEditTime: 2020-06-11 20:26:35
 * @Description: 
-->

> 原文链接

[https://leetcode.com/problems/daily-temperatures/](https://leetcode.com/problems/daily-temperatures/)

> 题目内容

Given a list of daily temperatures T, return a list such that, for each day in the input, tells you how many days you would have to wait until a warmer temperature. If there is no future day for which this is possible, put 0 instead.

For example, given the list of temperatures T = [73, 74, 75, 71, 69, 72, 76, 73], your output should be [1, 1, 4, 2, 1, 1, 0, 0].

**Note:** The length of temperatures will be in the range [1, 30000]. Each temperature will be an integer in the range [30, 100].

> 解题思路

```js
/**
 * @param {number[]} T
 * @return {number[]}
 */
var dailyTemperatures = function (T) {
  let len = T.length;
  for (let i = 0; i < len; i++) {
    let j = i + 1;
    while (j < len && T[i] >= T[j]) {
      j++;
    }
    T[i] = j >= len ? 0 : j - i;
  }
  return T;
};
```
