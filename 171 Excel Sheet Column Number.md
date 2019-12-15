<!--
 * @Author: FBB
 * @Date: 2019-12-15 14:12:04
 * @LastEditors: FBB
 * @LastEditTime: 2019-12-15 14:14:58
 * @Description:
 -->

> 原文链接

[https://leetcode.com/problems/excel-sheet-column-number/](https://leetcode.com/problems/excel-sheet-column-number/)

> 题目内容

Given a column title as appear in an Excel sheet, return its corresponding column number.

For example:

```
A -> 1
B -> 2
C -> 3
...
Z -> 26
AA -> 27
AB -> 28
...
```

**Example 1:**

```
Input: "A"
Output: 1
```

**Example 2:**

```
Input: "AB"
Output: 28
```

**Example 3:**

```
Input: "ZY"
Output: 701
```

> 解题思路

- 思路
  从尾到头，第 n 位的字母，数值基数为 26 的 n-1

```js
/**
 * @param {string} s
 * @return {number}
 */
var titleToNumber = function(s) {
  let arr = s.split("");
  let res = 0;
  arr.forEach((item, index) => {
    res += (item.charCodeAt() - 64) * Math.pow(26, arr.length - 1 - index);
  });
  return res;
};
```
