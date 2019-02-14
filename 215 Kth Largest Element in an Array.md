> 原文链接

[https://leetcode.com/problems/kth-largest-element-in-an-array/](https://leetcode.com/problems/kth-largest-element-in-an-array/)
> 题目内容

Find the kth largest element in an unsorted array. Note that it is the kth largest element in the sorted order, not the kth distinct element.

**Example 1**:
```
Input: [3,2,1,5,6,4] and k = 2
Output: 5
```
**Example 2**:
```
Input: [3,2,3,1,2,4,5,5,6] and k = 4
Output: 4
```
**Note**: 
You may assume k is always valid, 1 ≤ k ≤ array's length.

> 解题思路

```js
/**
 * @param {number[]} nums
 * @param {number} k
 * @return {number}
 */
var findKthLargest = function (nums, k) {
  let index = nums.length - k
  return __partition(nums, 0, nums.length - 1, index)
};

function __partition(arr, left, right, k) {
  if (left > right)
    return
  let standard = arr[left]
  let index = left
  for (let i = left + 1; i <= right; i++) {
    if (arr[i] < standard) {
      swap(arr, i, index + 1)
      index++
    }
  }
  swap(arr, left, index)
  if (k > index) {
    __partition(arr, index + 1, right, k)
  } else {
    __partition(arr, left, index - 1, k)
  }
  return arr[k]
}

function swap(arr, i, j) {
  let temp = arr[i];
  arr[i] = arr[j];
  arr[j] = temp;
}
```