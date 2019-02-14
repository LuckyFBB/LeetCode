> 原文链接

[https://leetcode.com/problems/sort-colors/](https://leetcode.com/problems/sort-colors/)
> 题目内容

Given an array with n objects colored red, white or blue, sort them in-place so that objects of the same color are adjacent, with the colors in the order red, white and blue.

Here, we will use the integers 0, 1, and 2 to represent the color red, white, and blue respectively.

**Note**: You are not suppose to use the library's sort function for this problem.

**Example**:
```t
Input: [2,0,2,1,1,0]
Output: [0,0,1,1,2,2]
```
**Follow up**:

A rather straight forward solution is a two-pass algorithm using counting sort.
First, iterate the array counting number of 0's, 1's, and 2's, then overwrite array with total number of 0's, then 1's and followed by 2's.
Could you come up with a one-pass algorithm using only constant space?

> 解题思路

思路1：使用单路快排

```js
/**
 * @param {number[]} nums
 * @return {void} Do not return anything, modify nums in-place instead.
 */
var sortColors = function (nums) {
  __quickSort(nums, 0, nums.length)
};

function __quickSort(arr, left, right) {
  if (left >= right) {
    return;
  }
  let index = __partition(arr, left, right);
  __quickSort(arr, left, index - 1);
  __quickSort(arr, index + 1, right);
}

function __partition(arr, left, right) {
  let standard = arr[left];
  let index = left;
  for (let i = left + 1; i <= right; i++) {
    if (arr[i] < standard) {
      swap(arr, i, index + 1);
      index++;
    }
  }
  swap(arr, left, index);
  return index;
}

function swap(arr, i, j) {
  let temp = arr[i];
  arr[i] = arr[j];
  arr[j] = temp;
}
```

思路2：通用三路排序
```js
/**
 * @param {number[]} nums
 * @return {void} Do not return anything, modify nums in-place instead.
 */
var sortColors = function (nums) {
  __quickSortThreeWays(nums, 0, nums.length - 1)
};

function __quickSortThreeWays(arr, left, right) {
  if (left >= right) {
    return;
  }
  let standard = arr[left];
  let lt = left;   //arr[left...lt]<standard
  let i = left + 1;    //arr[lt+1...i]=standard
  let gt = right + 1;   //arr[gt...right]>standard
  while (i < gt) {
    if (arr[i] < standard) {
      swap(arr, i, lt + 1);
      lt++;
      i++;
    } else if (arr[i] > standard) {
      swap(arr, i, gt - 1);
      gt--;
    } else {
      i++;
    }
  }
  swap(arr, left, lt);
  __quickSortThreeWays(arr, left, lt - 1);
  __quickSortThreeWays(arr, gt, right);
}

function swap(arr, i, j) {
  let temp = arr[i];
  arr[i] = arr[j];
  arr[j] = temp;
}
```

思路3：基于012的一次三路排序
```js
/**
 * @param {number[]} nums
 * @return {void} Do not return anything, modify nums in-place instead.
 */
var sortColors = function (nums) {
  let zero = -1;//nums[0...zero]===0
  let two = nums.length;//nums[two...n-1]===2
  let i = 0;
  while (i < two) {
    if (nums[i] === 1) {
      i++
    } else if (nums[i] < 1) {
      swap(nums, i, ++zero)
      i++
    } else {
      swap(nums, i, --two)
    }
  }
};

function swap(arr, i, j) {
  let temp = arr[i];
  arr[i] = arr[j];
  arr[j] = temp;
}
```