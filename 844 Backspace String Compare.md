<!--
 * @Author: FBB
 * @Date: 2020-04-09 21:56:46
 * @LastEditors: FBB
 * @LastEditTime: 2020-04-11 14:17:42
 * @Description:
 -->

> 原文链接

[https://leetcode.com/problems/backspace-string-compare/](https://leetcode.com/problems/backspace-string-compare/)

> 题目内容

Given two strings S and T, return if they are equal when both are typed into empty text editors. # means a backspace character.

**Example 1:**

```
Input: S = "ab#c", T = "ad#c"
Output: true
Explanation: Both S and T become "ac".
```

**Example 2:**

```
Input: S = "ab##", T = "c#d#"
Output: true
Explanation: Both S and T become "".
```

**Example 3:**

```
Input: S = "a##c", T = "#a#c"
Output: true
Explanation: Both S and T become "c".
```

**Example 4:**

```
Input: S = "a#c", T = "b"
Output: false
Explanation: S becomes "c" while T becomes "b".
```

**Note:**

1. 1 <= S.length <= 200
2. 1 <= T.length <= 200
3. S and T only contain lowercase letters and '#' characters.

**Follow up:**

- Can you solve it in O(N) time and O(1) space?

> 解题思路

- 思路 1
  对#字符前的数据进行删除之后得到字符串，然后再两者比较

```js
/**
 * @param {string} S
 * @param {string} T
 * @return {boolean}
 */
var backspaceCompare = function (S, T) {
  return removeEmpty(S) === removeEmpty(T);
};
var removeEmpty = function (str) {
  let arr = str.split("");
  while (arr.includes("#")) {
    const idx = arr.indexOf("#");
    idx === 0 ? arr.splice(idx, 1) : arr.splice(idx - 1, 2);
  }
  return arr.join("");
};
```

- 思路 2
  使用栈，遇到#将栈的顶部元素删除，否在压入栈中，最后返回栈

```js
/**
 * @param {string} S
 * @param {string} T
 * @return {boolean}
 */
var backspaceCompare = function (S, T) {
  return removeEmpty(S) === removeEmpty(T);
};
var removeEmpty = function (str) {
  const stack = [];
  for (const s of str) {
    s === "#" ? stack.pop() : stack.push(s);
  }
  return stack.join("");
};
```
