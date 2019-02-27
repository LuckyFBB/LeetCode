> 原文链接

[https://leetcode.com/problems/remove-duplicates-from-sorted-array/](https://leetcode.com/problems/remove-duplicates-from-sorted-array/)
> 题目内容

Given an unsorted integer array, find the smallest missing positive integer.

**Example 1:**
```
Input: [1,2,0]
Output: 3
```

**Example 2:**
```
Input: [3,4,-1,1]
Output: 2
```

**Example 3:**
```
Input: [7,8,9,11,12]
Output: 1
```

**Note:**

Your algorithm should run in O(n) time and uses constant extra space.
> 解题思路

思路1：先排序在遍历
```js
/**
 * @param {number[]} nums
 * @return {number}
 */
var firstMissingPositive = function(nums) {
  nums = nums.filter(item => item > 0)
  if (nums.length) {
    nums.sort((a, b) => a - b)
    if (nums[0] !== 1) {
      return 1
    } else {
      for (let i = 1; i < nums.length; i++) {
        if (nums[i] - nums[i - 1] !== 1) {
          return nums[i - 1] + 1
        }
      }
      return nums.pop() + 1
    }
  } else {
    return 1
  }
};
```

思路2：在进行选择排序的过程中，进行计算比较
```js
/**
 * @param {number[]} nums
 * @return {number}
 */
var firstMissingPositive = function(nums) {
  nums = nums.filter(item => item > 0)   //过滤掉负数
  let len = nums.length
  for (let i = 0; i < len; i++) {
    let minIndex = i
    for (let j = i + 1; j < len; j++) {
      if (nums[j] < nums[minIndex]) {     // 寻找最小的数
        minIndex = j               // 将最小数的索引保存
      }
    }
    swap(nums, i, minIndex)
    if (nums[i] > 1 && i == 0) {
      return 1
    } else {
      if (nums[i] - nums[i - 1] > 1) {
        return nums[i - 1] + 1
      }
    }
  }
  return len ? nums.pop() + 1 : 1
}

function swap(arr, i, j) {
  let temp = arr[i];
  arr[i] = arr[j];
  arr[j] = temp;
}
```