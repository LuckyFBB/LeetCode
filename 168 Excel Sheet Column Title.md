> 原文链接

[https://leetcode.com/problems/excel-sheet-column-title/](https://leetcode.com/problems/excel-sheet-column-title/)

> 题目内容

Given a positive integer, return its corresponding column title as appear in an Excel sheet.

**For example:**
1 -> A
2 -> B
3 -> C
...
26 -> Z
27 -> AA
28 -> AB
...

**Example 1:**

```
Input: 1
Output: "A"
```

**Example 2:**

```
Input: 28
Output: "AB"
```

**Example 3:**

```
Input: 701
Output: "ZY"
```

> 解题思路

- 思路一
  递归

```js
/**
 * @param {number} n
 * @return {string}
 */

var convertToTitle = function(n) {
  n = n - 1;
  while (n >= 0 && n <= 25) {
    return String.fromCharCode(65 + n);
  }
  return convertToTitle(parseInt(n / 26)) + convertToTitle((n % 26) + 1);
};
```

- 思路二
  循环

```js
/**
 * @param {number} n
 * @return {string}
 */

var convertToTitle = function(n) {
  let title = "";
  let rem;
  while (n) {
    rem = (n - 1) % 26;
    n = (n - 1 - rem) / 26;
    title += String.fromCharCode(65 + rem);
    return title;
  }
};
```
