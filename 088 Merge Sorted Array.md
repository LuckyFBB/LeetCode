> 原文链接

[https://leetcode.com/problems/merge-sorted-array/](https://leetcode.com/problems/merge-sorted-array/)
> 题目内容

Given two sorted integer arrays nums1 and nums2, merge nums2 into nums1 as one sorted array.

**Note**:

The number of elements initialized in nums1 and nums2 are m and n respectively.
You may assume that nums1 has enough space (size that is greater or equal to m + n) to hold additional elements from nums2.

**Example**:
```t
Input:
nums1 = [1,2,3,0,0,0], m = 3
nums2 = [2,5,6],       n = 3

Output: [1,2,2,3,5,6]
```
> 解题思路

```js
/**
 * @param {number[]} nums1
 * @param {number} m
 * @param {number[]} nums2
 * @param {number} n
 * @return {void} Do not return anything, modify nums1 in-place instead.
 */
var merge = function (nums1, m, nums2, n) {
  let len = m + n - 1
  m--
  n--
  while (m >= 0 && n >= 0) {
    if (nums1[m] >= nums2[n]) {
      nums1[len--] = nums1[m--]
    } else {
      nums1[len--] = nums2[n--]
    }
  }
  while (n >= 0) {
    nums1[len--] = nums2[n--]
  }
  return nums1
};
```