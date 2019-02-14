> 原文链接

[https://leetcode.com/problems/palindrome-number/](https://leetcode.com/problems/palindrome-number/)
> 题目内容

Determine whether an integer is a palindrome. An integer is a palindrome when it reads the same backward as forward.

Example 1:
```t
Input: 121
Output: true
```
Example 2:
```t
Input: -121
Output: false
Explanation: From left to right, it reads -121. From right to left, it becomes 121-. Therefore it is not a palindrome.
```
Example 3:
```t
Input: 10
Output: false
Explanation: Reads 01 from right to left. Therefore it is not a palindrome.
```
Follow up:

Coud you solve it without converting the integer to a string?

> 解题思路

转为字符串再转为数组倒序

时间复杂度O(1)

```js
/**
 * @param {number} x
 * @return {boolean}
 */
var isPalindrome = function(x) {
  let str=x.toString();
  let reserveStr=str.split('').reverse().join('');
  if(str===reserveStr) {
    return true;
  }
  return false;
};
```