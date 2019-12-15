> 原文链接

[https://leetcode.com/problems/happy-number/](https://leetcode.com/problems/happy-number/)

> 题目内容

Write an algorithm to determine if a number is "happy".

A happy number is a number defined by the following process: Starting with any positive integer, replace the number by the sum of the squares of its digits, and repeat the process until the number equals 1 (where it will stay), or it loops endlessly in a cycle which does not include 1. Those numbers for which this process ends in 1 are happy numbers.

**Example:**

```
Input: 19
Output: true
Explanation:
12 + 92 = 82
82 + 22 = 68
62 + 82 = 100
12 + 02 + 02 = 1
```

> 解题思路

- 思路一
  使用数组来记录当前值是否参与过计算，如果参与过则直接返回结果；否则执行计算，并添加到参与计算的数组中。

```js
/**
 * @param {number} n
 * @return {boolean}
 */
var isHappy = function(n) {
  const before = [];
  while (n !== 1 && !before[n]) {
    before[n] = true;
    n = n
      .toString()
      .split("")
      .reduce(function(prev, next) {
        return prev + Math.pow(next, 2);
      }, 0);
  }
  return n === 1;
};
```

- 思路二
  采用相同的思想，但是使用新的数据结构

```js
/**
 * @param {number} n
 * @return {boolean}
 */
var isHappy = function(n) {
  if (n < 1) return false;
  let set = new Set();
  while (!set.has(n)) {
    set.add(n);
    let s = n.toString();
    n = 0;
    for (let i = 0; i < s.length; ++i) {
      n += Math.pow(s[i], 2);
    }
    if (n == 1) return true;
  }
  return false;
};
```
