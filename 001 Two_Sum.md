> 原文链接

[https://leetcode.com/problems/two-sum/](https://leetcode.com/problems/two-sum/)
> 题目内容

Given an array of integers, return indices of the two numbers such that they add up to a specific target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

Example:
```
Given nums = [2, 7, 11, 15], target = 9,

Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].
```
> 解题思路

思路1: 两层循环，暴力解法
```js
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
var twoSum = function (nums, target) {
  for (let i = 0; i < nums.length - 1; i++) {
    for (let j = i + 1; j < nums.length; j++) {
      if (nums[i] + nums[j] === target)
        return [i, j]
    }
  }
};
```

思路2: 先定义一个Array类型的数据结构obj，它的index为target - numbers[i]，value为索引。然后每次都看看obj[numbers[i]] 是否存在，如果存在，那我们就找到了这样的一组数据，返回当前索引以及obj[numbers[i]]。

时间复杂度O(N)

```js
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
var twoSum = function (nums, target) {
  let obj = [];
  for (let i = 0; i < nums.length; i++) {
    const item = nums[i];
    if (obj[item] >= 0) {
      return [obj[item], i]
    } else {
      obj[target - item] = i;
    }
  }
};
```