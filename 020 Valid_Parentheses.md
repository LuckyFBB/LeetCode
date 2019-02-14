> 原文链接

[https://leetcode.com/problems/valid-parentheses/](https://leetcode.com/problems/valid-parentheses/)
> 题目内容

Given a string containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.

An input string is valid if:

Open brackets must be closed by the same type of brackets.
Open brackets must be closed in the correct order.
Note that an empty string is also considered valid.

Example 1:
```t
Input: "()"
Output: true
```
Example 2:
```t
Input: "()[]{}"
Output: true
```
Example 3:
```t
Input: "(]"
Output: false
```
Example 4:
```t
Input: "([)]"
Output: false
```
Example 5:
```t
Input: "{[]}"
Output: true
```

> 解题思路1

数组暴力解法

时间复杂度 O(N)

```js
/**
 * @param {string} s
 * @return {boolean}
 */
var isValid = function (s) {
  if (!s) {
    return true;
  }
  let arr = [];
  for (let i = 0; i < s.length; i++) {
    let currentChar = s.charAt(i);
    if (currentChar === '(' || currentChar === '[' || currentChar === '{') {
      arr.push(currentChar)
    } else if (!arr.length) {
      return false
    } else {
      let pre = arr.pop();
      if (pre === '(' && currentChar !== ')') {
        return false;
      }
      if (pre === '{' && currentChar !== '}') {
        return false;
      }
      if (pre === '[' && currentChar !== ']') {
        return false;
      }
    }
  }
  return !arr.length
};
```

> 解题思路2

使用栈方法，引入对象

时间复杂度O(N)
```js
/**
 * @param {string} str
 * @return {boolean}
 */
let map = {
  '(': ')',
  '{': '}',
  '[': ']'
}
var isValid = function (str) {
  let stack = [];
  for (let i = 0; i < str.length; i++) {
    let char = str[i];
    if (map[char]) {
      stack.push(char)
    } else {
      if (map[stack.pop()] !== char) {
        return false
      }
    }
  }
  return !stack.length;
}
```