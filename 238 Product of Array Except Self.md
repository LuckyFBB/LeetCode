<!--
 * @Author: FBB
 * @Date: 2020-04-15 21:23:08
 * @LastEditors: FBB
 * @LastEditTime: 2020-04-15 21:26:03
 * @Description:
 -->

> 原文链接

[https://leetcode.com/problems/invert-binary-tree/](https://leetcode.com/problems/invert-binary-tree/)

> 题目内容

Given an array nums of n integers where n > 1, return an array output such that output[i] is equal to the product of all the elements of nums except nums[i].

**Example:**

```
Input:  [1,2,3,4]
Output: [24,12,8,6]
Constraint: It's guaranteed that the product of the elements of any prefix or suffix of the array (including the whole array) fits in a 32 bit integer.
```

**Note:** Please solve it without division and in O(n).

**Follow up:**
Could you solve it with constant space complexity? (The output array does not count as extra space for the purpose of space complexity analysis.)

> 解题思路

- 思路 1
  使用 reduce 来实现，但是耗时较长

```js
/**
 * @param {number[]} nums
 * @return {number[]}
 */
var productExceptSelf = function (nums) {
  const res = [];
  nums.map((ele, index, arr) => {
    ele = arr.slice();
    ele.splice(index, 1);
    res.push(ele.reduce((prev, curr) => (curr *= prev)));
  });
  return res;
};
```
