> 原文链接

[https://leetcode.com/problems/length-of-last-word/](https://leetcode.com/problems/length-of-last-word/)
> 题目内容

Given a string s consists of upper/lower-case alphabets and empty space characters ' ', return the length of last word in the string.

If the last word does not exist, return 0.

Note: A word is defined as a character sequence consists of non-space characters only.

Example:
```
Input: "Hello World"
Output: 5
```

> 解题思路

- 将数组以空格分割，找到最后一个字符串输出长度
- 注意以空格结尾以及输入空字符串

时间复杂度 O(N)

```js
/**
 * @param {string} s
 * @return {number}
 */
var lengthOfLastWord = function (str) {
  let tempArr = str.split(' ').filter(value => value != '');
  return tempArr.length ? tempArr.pop().length : 0;
};
```