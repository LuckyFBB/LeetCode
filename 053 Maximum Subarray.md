> 原文链接

[https://leetcode.com/problems/maximum-subarray/](https://leetcode.com/problems/maximum-subarray/)
> 题目内容

Given an integer array nums, find the contiguous subarray (containing at least one number) which has the largest sum and return its sum.

**Example:**
```
Input: [-2,1,-3,4,-1,2,1,-5,4],
Output: 6
Explanation: [4,-1,2,1] has the largest sum = 6.
```
**Follow up:**

If you have figured out the O(n) solution, try coding another solution using the divide and conquer approach, which is more subtle.

> 解题思路

```js
/**
 * @param {number[]} nums
 * @return {number}
 */
var maxSubArray = function (nums) {
  let sum = 0
  return nums.reduce((max, curr) => {
    sum = curr + (sum > 0 ? sum : 0);
    return Math.max(max, sum);
  }, -Number.MAX_VALUE)
};
```