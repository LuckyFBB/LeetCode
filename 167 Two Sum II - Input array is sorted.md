> 原文链接

[https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/)
> 题目内容

Given an array of integers that is already sorted in ascending order, find two numbers such that they add up to a specific target number.

The function twoSum should return indices of the two numbers such that they add up to the target, where index1 must be less than index2.

**Note**:

- Your returned answers (both index1 and index2) are not zero-based.
- You may assume that each input would have exactly one solution and you may not use the same element twice.
**Example**:
```
Input: numbers = [2,7,11,15], target = 9
Output: [1,2]
Explanation: The sum of 2 and 7 is 9. Therefore index1 = 1, index2 = 2.
```
> 解题思路

思路：两头往中间找

```js
/**
 * @param {number[]} numbers
 * @param {number} target
 * @return {number[]}
 */
var twoSum = function (numbers, target) {
  let [left, right] = [0, numbers.length - 1]
  while (left < right) {
    if (numbers[left] + numbers[right] === target) {
      return [left, right].map(item => item + 1);
    } else if (numbers[left] + numbers[right] > target) {
      right--
    } else {
      left++
    }
  }
};
```