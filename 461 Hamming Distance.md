<!--
 * @Author: FBB
 * @Date: 2020-08-11 21:27:21
 * @LastEditors: FBB
 * @LastEditTime: 2020-08-11 21:28:58
 * @Description:
-->

> 原文链接

[https://leetcode.com/problems/hamming-distance/](https://leetcode.com/problems/hamming-distance/)

> 题目内容

The Hamming distance between two integers is the number of positions at which the corresponding bits are different.

Given two integers x and y, calculate the Hamming distance.

**Note:**
0 ≤ x, y < 231.

**Example:**

```
Input: x = 1, y = 4

Output: 2

Explanation:
1   (0 0 0 1)
4   (0 1 0 0)
       ↑   ↑

The above arrows point to positions where the corresponding bits are different.
```

> 解题思路

- & : 按二进制位进行 与运算，相同位同时为 1 时结果为 1，否则为 0
- | : 按二进制位进行 或运算，相同位有一个为 1 时结果为 1，否则为 0
- ^ : 按二进制位进行 异或运算，相同位相同时结果为 0，否则为 1
- > > : 右移运算是将一个二进制位的操作数按指定移动的位数向右移动，移出位被丢弃，左边移出的空位或者一律补 0
- << : 左移运算是将一个二进制位的操作数按指定移动的位数向左移位，移出位被丢弃，右边的空位一律补 0

```js
/**
 * @param {number} x
 * @param {number} y
 * @return {number}
 */
var hammingDistance = function (x, y) {
  let ans = 1;
  while (x !== 0 || y !== 0) {
    if ((x & 1) !== (y & 1)) {
      ans++;
    }
    x >>= 1;
    y >>= 1;
  }
  return ans;
};
```
