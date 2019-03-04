> 原文链接

[https://leetcode.com/problems/single-number/](https://leetcode.com/problems/single-number/)
> 题目内容

GGiven a non-empty array of integers, every element appears twice except for one. Find that single one.

**Note:**

Your algorithm should have a linear runtime complexity. Could you implement it without using extra memory?

**Example 1:**
```
Input: [2,2,1]
Output: 1
```

**Example 2:**
```
Input: [4,1,2,1,2]
Output: 4
```

> 解题思路

```js
/**
 * @param {number[]} nums
 * @return {number}
 */
var singleNumber = function (nums) {
  let number = [nums[0]]
  for (let i = 1; i < nums.length; i++) {
    let index = number.indexOf(nums[i])
    if (index === -1) {
      number.push(nums[i])
    } else {
      number.splice(index, 1)
    }
  }
  return number[0]
};
```