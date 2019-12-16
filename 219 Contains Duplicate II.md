> 原文链接

[https://leetcode.com/problems/contains-duplicate-ii/](https://leetcode.com/problems/contains-duplicate-ii/)

> 题目内容

Given an array of integers and an integer k, find out whether there are two distinct indices i and j in the array such that nums[i] = nums[j] and the absolute difference between i and j is at most k.

**Example 1:**

```
Input: nums = [1,2,3,1], k = 3
Output: true
```

**Example 2:**

```
Input: nums = [1,0,1,1], k = 1
Output: true
```

**Example 3:**

```
Input: nums = [1,2,3,1,2,3], k = 2
Output: false
```

> 解题思路

- 思路一
  使用 map 判断是否含有当前数据(去重思想)

```js
/**
 * @param {number[]} nums
 * @param {number} k
 * @return {boolean}
 */
var containsNearbyDuplicate = function(nums, k) {
  let map = new Map();
  for (let i = 0; i < nums.length; i++) {
    const item = nums[i];
    if (map.has(item) && i - map.get(item) <= k) {
      return true;
    } else {
      map.set(item, i);
    }
  }
  return false;
};
```
