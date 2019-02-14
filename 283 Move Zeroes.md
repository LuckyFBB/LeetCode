> 原文链接

[https://leetcode.com/problems/move-zeroes/](https://leetcode.com/problems/move-zeroes/)
> 题目内容

Given an array nums, write a function to move all 0's to the end of it while maintaining the relative order of the non-zero elements.
```
Example:

Input: [0,1,0,3,12]
Output: [1,3,12,0,0]
```
Note:

1. You must do this in-place without making a copy of the array.
2. Minimize the total number of operations.


> 解题思路

循环遍历  
算法复杂度O(n)  
空间复杂度O(n)

```js
/**
 * @param {number[]} nums
 * @return {void} Do not return anything, modify nums in-place instead.
 */
var moveZeroes = function (nums) {
  let nonZero = []
  for (let i = 0; i < nums.length; i++) {
    if (nums[i]) {
      nonZero.push(nums[i])
    }
  }
  for (let i = 0; i < nonZero.length; i++) {
    nums[i] = nonZero[i]
  }
  for (let i = nonZero.length; i < nums.length; i++) {
    nums[i] = 0
  }
  return nums
};
```