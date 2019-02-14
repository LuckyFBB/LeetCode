> 原文链接

[https://leetcode.com/problems/reverse-integer/](https://leetcode.com/problems/reverse-integer/)
> 题目内容

Given a 32-bit signed integer, reverse digits of an integer.

Example 1:
```
Input: 123
Output: 321
```
Example 2:
```
Input: -123
Output: -321
```
Example 3:
```
Input: 120
Output: 21
```
Note:
Assume we are dealing with an environment which could only store integers within the 32-bit signed integer range: [−231,  231 − 1]. For the purpose of this problem, assume that your function returns 0 when the reversed integer overflows.

> 解题思路

数字转为字符串再转为数组，翻转再转回数字

时间复杂度O(1)

```js
/**
 * @param {number} x
 * @return {number}
 */
var reverse = function (x) {
  let num = parseInt(x.toString().split('').reverse().join(''));
  if (num > Math.pow(2, 31)) {
    return 0
  }
  if (x < 0) {
    return num * (-1);
  } else {
    return num
  }
};
```