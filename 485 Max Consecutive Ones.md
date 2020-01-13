> 原文链接

[https://leetcode.com/problems/max-consecutive-ones/](https://leetcode.com/problems/max-consecutive-ones/)

> 题目内容

Given a binary array, find the maximum number of consecutive 1s in this array.

**Example 1:**

```
Input: [1,1,0,1,1,1]
Output: 3
Explanation: The first two digits or the last three digits are consecutive 1s.
    The maximum number of consecutive 1s is 3.
```

Note:

- The input array will only contain 0 and 1.
- The length of input array is a positive integer and will not exceed 10,000

> 解题思路

1. for 循环

```js
/**
 * @param {number[]} nums
 * @return {number}
 */
var findMaxConsecutiveOnes = function(nums) {
  let num = 0;
  let result = 0;
  for (let i = 0; i < nums.length; i++) {
    result = Math.max(result, (num = nums[i] == 0 ? 0 : num + 1));
  }
  return result;
};
```

2. 使用 reduce 完成

```js
/**
 * @param {number[]} nums
 * @return {number}
 */
var findMaxConsecutiveOnes = function(nums) {
  let result = 0;
  nums.reduce((prev, curr) => {
    prev = curr === 1 ? prev + 1 : 0;
    result = Math.max(result, prev);
    return prev;
  }, 0);
  return result;
};
```
