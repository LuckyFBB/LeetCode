<!--
 * @Author: FBB
 * @Date: 2020-05-07 20:33:09
 * @LastEditors: FBB
 * @LastEditTime: 2020-05-07 20:34:48
 * @Description:
 -->

> 原文链接

[https://leetcode.com/problems/top-k-frequent-elements/](https://leetcode.com/problems/top-k-frequent-elements/)

> 题目内容

Given a non-empty array of integers, return the k most frequent elements.

**Example 1:**

```
Input: nums = [1,1,1,2,2,3], k = 2
Output: [1,2]
```

**Example 2:**

```
Input: nums = [1], k = 1
Output: [1]
```

**Note:**

- You may assume k is always valid, 1 ≤ k ≤ number of unique elements.
- Your algorithm's time complexity must be better than O(n log n), where n is the array's size.
- It's guaranteed that the answer is unique, in other words the set of the top k frequent elements is unique.
- You can return the answer in any order.

> 解题思路

```js
/**
 * @param {number[]} nums
 * @param {number} k
 * @return {number[]}
 */
var topKFrequent = function (nums, k) {
  const map = new Map();
  nums.forEach((item) => map.set(item, map.get(item) ? map.get(item) + 1 : 1));
  return [...map]
    .sort((a, b) => b[1] - a[1])
    .slice(0, k)
    .map((item) => item[0]);
};
```
