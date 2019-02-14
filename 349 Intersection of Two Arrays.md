> 原文链接

[https://leetcode.com/problems/intersection-of-two-arrays/](https://leetcode.com/problems/intersection-of-two-arrays/)
> 题目内容

Given two arrays, write a function to compute their intersection.

**Example 1**:

Input: nums1 = [1,2,2,1], nums2 = [2,2]
Output: [2]
**Example 2**:

Input: nums1 = [4,9,5], nums2 = [9,4,9,8,4]
Output: [9,4]
**Note**:

- Each element in the result must be unique.
- The result can be in any order.

> 解题思路

```js
/**
 * @param {number[]} nums1
 * @param {number[]} nums2
 * @return {number[]}
 */
var intersection = function (nums1, nums2) {
  let record = new Set();
  let result = new Set();
  for (let i = 0; i < nums1.length; i++) {
    record.add(nums1[i])
  }
  for (let i = 0; i < nums2.length; i++) {
    if (record.has(nums2[i])) {
      result.add(nums2[i])
    }
  }
  return Array.from(result)
};
```

```js
/**
 * @param {number[]} nums1
 * @param {number[]} nums2
 * @return {number[]}
 */
var intersection = function (nums1, nums2) {
  let result = new Set();
  if (nums1.length > nums2.length)
    [nums1, nums2] = [nums2, nums1]
  for (let i = 0; i < nums1.length; i++) {
    if (nums2.includes(nums1[i])) {
      result.add(nums1[i])
    }
  }
  return Array.from(result)
};
```