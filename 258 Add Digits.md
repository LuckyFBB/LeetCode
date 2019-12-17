> 原文链接

[https://leetcode.com/problems/add-digits/](https://leetcode.com/problems/add-digits/)

> 题目内容

Given a non-negative integer num, repeatedly add all its digits until the result has only one digit.

**Example:**

```
Input: 38
Output: 2
Explanation: The process is like: 3 + 8 = 11, 1 + 1 = 2.
Since 2 has only one digit, return it.
```

**Follow up:**
Could you do it without any loop/recursion in O(1) runtime?

> 解题思路

```js
/**
 * @param {number} num
 * @return {number}
 */
var addDigits = function(num) {
  while (num > 9) {
    let res = 0;
    num
      .toString()
      .split("")
      .forEach(item => {
        res += parseInt(item);
      });
    num = res;
  }
  return num;
};
```
