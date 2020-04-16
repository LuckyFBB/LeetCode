<!--
 * @Author: FBB
 * @Date: 2020-04-16 22:26:19
 * @LastEditors: FBB
 * @LastEditTime: 2020-04-16 22:29:22
 * @Description:
 -->

> 原文链接

[https://leetcode.com/problems/valid-parenthesis-string/](https://leetcode.com/problems/valid-parenthesis-string/)

> 题目内容

Given a string containing only three types of characters: '(', ')' and '\*', write a function to check whether this string is valid. We define the validity of a string by these rules:

Any left parenthesis '(' must have a corresponding right parenthesis ')'.
Any right parenthesis ')' must have a corresponding left parenthesis '('.
Left parenthesis '(' must go before the corresponding right parenthesis ')'.
'\*' could be treated as a single right parenthesis ')' or a single left parenthesis '(' or an empty string.
An empty string is also valid.
**Example 1:**

```
Input: "()"
Output: True
```

**Example 2:**

```
Input: "(*)"
Output: True
```

**Example 3:**

```
Input: "(*))"
Output: True
```

**Note:**
The string size will be in the range [1, 100].

> 解题思路

- 思路 1
  先从左往右检查是否匹配，然后再从右往左检查。

```js
/**
 * @param {string} s
 * @return {boolean}
 */
var checkValidString = function (s) {
  let leftStack = [];
  for (const char of s) {
    if (char === "(" || char === "*") {
      leftStack.push(char);
    } else {
      if (leftStack.length) {
        leftStack.pop();
      } else {
        return false;
      }
    }
  }
  leftStack = [];
  for (const char of s.split("").reverse().join("")) {
    if (char === ")" || char === "*") {
      leftStack.push(char);
    } else {
      if (leftStack.length) {
        leftStack.pop();
      } else {
        return false;
      }
    }
  }
  return true;
};
```
