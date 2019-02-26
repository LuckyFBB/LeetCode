> 原文链接

[https://leetcode.com/problems/maximum-gap/](https://leetcode.com/problems/maximum-gap/)
> 题目内容

Given an unsorted array, find the maximum difference between the successive elements in its sorted form.

Return 0 if the array contains less than 2 elements.

**Example 1:**
```
Input: [3,6,9,1]
Output: 3
Explanation: The sorted form of the array is [1,3,6,9], either
             (3,6) or (6,9) has the maximum difference 3.
```
             
**Example 2:**
```
Input: [10]
Output: 0
Explanation: The array contains less than 2 elements, therefore return 0.
```

**Note:**

- You may assume all elements in the array are non-negative integers and fit in the 32-bit signed integer range.
- Try to solve it in linear time/space.

> 解题思路

思路1：先排序再计算间距值
```js
/**
 * @param {number[]} nums
 * @return {number}
 */
var maximumGap = function(nums) {
  //小于2 返回0
  if (nums.length < 2) {
    return 0
  }
  let max = 0
  nums.sort((a, b) => a - b)
  for (let index = 0; index < nums.length - 1; index++) {
    let temp = nums[index + 1] - nums[index]
    if (temp > max) {
      max = temp
    }
  }
  return max
};
```

思路2：在冒泡的过程中计算间距值

```js
/**
 * @param {number[]} nums
 * @return {number}
 */
var maximumGap = function(nums) {
  if (nums.length < 2) {
    return 0
  }
  let max = 0
  let len = nums.length - 1
  nums.sort((a, b) => a - b)
  for (let i = len; i >= 0; i--) {
    for (let j = 0; j < i; j++) {
      if (nums[j] > nums[j + 1]) {
        let temp = nums[j]
        nums[j] = nums[j + 1]
        nums[j + 1] = temp
      }
    }
    if (i < len) {
      max = max > nums[i + 1] - nums[i] ? max : nums[i + 1] - nums[i]
    }
  }
  return max
};
```