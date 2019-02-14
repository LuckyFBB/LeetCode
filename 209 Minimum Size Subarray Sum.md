> 原文链接

[https://leetcode.com/problems/minimum-size-subarray-sum/](https://leetcode.com/problems/minimum-size-subarray-sum/)
> 题目内容

Given an array of n positive integers and a positive integer s, find the minimal length of a contiguous subarray of which the sum ≥ s. If there isn't one, return 0 instead.

**Example**: 

Input: s = 7, nums = [2,3,1,2,4,3]
Output: 2
Explanation: the subarray [4,3] has the minimal length under the problem constraint.
**Follow up**:
If you have figured out the O(n) solution, try coding another solution of which the time complexity is O(n log n). 

> 解题思路

```js
/**
 * @param {number} s
 * @param {number[]} nums
 * @return {number}
 */
var minSubArrayLen = function (s, nums) {
  let left = 0;
  let right = -1;   //nums[left...right]为滑动的窗口
  let res = nums.length + 1;
  let sum = 0;
  while (left < nums.length - 1) {
    if (sum < s && right < nums.length - 1) {
      sum += nums[++right]
    } else {
      sum -= nums[left++]
    }
    if (sum >= s) {
      res = Math.min(res, right - left + 1)
    }
  }
  return res === nums.length + 1 ? 0 : res
};
```