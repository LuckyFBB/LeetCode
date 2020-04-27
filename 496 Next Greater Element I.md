<!--
 * @Author: FBB
 * @Date: 2020-04-27 15:29:31
 * @LastEditors: FBB
 * @LastEditTime: 2020-04-27 15:31:38
 * @Description:
 -->

> 原文链接

[https://leetcode.com/problems/next-greater-element-i/](https://leetcode.com/problems/next-greater-element-i/)

> 题目内容

You are given two arrays (without duplicates) nums1 and nums2 where nums1’s elements are subset of nums2. Find all the next greater numbers for nums1's elements in the corresponding places of nums2.

The Next Greater Number of a number x in nums1 is the first greater number to its right in nums2. If it does not exist, output -1 for this number.

**Example 1:**

```
Input: nums1 = [4,1,2], nums2 = [1,3,4,2].
Output: [-1,3,-1]
Explanation:
    For number 4 in the first array, you cannot find the next greater number for it in the second array, so output -1.
    For number 1 in the first array, the next greater number for it in the second array is 3.
    For number 2 in the first array, there is no next greater number for it in the second array, so output -1.
```

**Example 2:**

```
Input: nums1 = [2,4], nums2 = [1,2,3,4].
Output: [3,-1]
Explanation:
    For number 2 in the first array, the next greater number for it in the second array is 3.
    For number 4 in the first array, there is no next greater number for it in the second array, so output -1.
```

**Note:**
All elements in nums1 and nums2 are unique.
The length of both nums1 and nums2 would not exceed 1000.

> 解题思路

- 思路 1
  for 循环

```js
/**
 * @param {number[]} nums1
 * @param {number[]} nums2
 * @return {number[]}
 */
var nextGreaterElement = function (nums1, nums2) {
  const result = [];
  nums1.forEach((item) => {
    let index = nums2.indexOf(item);
    let arr = nums2.slice(index);
    for (let j = 0; j < arr.length; j++) {
      const element = arr[j];
      if (element > item) {
        result.push(element);
        break;
      }
      if (j === arr.length - 1) {
        result.push(-1);
      }
    }
  });
  return result;
};
```
