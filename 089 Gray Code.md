> 原文链接

[https://leetcode.com/problems/gray-code/](https://leetcode.com/problems/gray-code/)
> 题目内容

The gray code is a binary numeral system where two successive values differ in only one bit.

Given a non-negative integer n representing the total number of bits in the code, print the sequence of gray code. A gray code sequence must begin with 0.

**Example 1:**
```
Input: 2
Output: [0,1,3,2]
Explanation:
00 - 0
01 - 1
11 - 3
10 - 2

For a given n, a gray code sequence may not be uniquely defined.
For example, [0,2,3,1] is also a valid gray code sequence.

00 - 0
10 - 2
11 - 3
01 - 1
```
**Example 2:**
```
Input: 0
Output: [0]
Explanation: We define the gray code sequence to begin with 0.
             A gray code sequence of n has size = 2n, which for n = 0 the size is 20 = 1.
             Therefore, for n = 0 the gray code sequence is [0].
```
> 解题思路

```js
/**
 * @param {number} n
 * @return {number[]}
 */
var grayCode = function (n) {
  const ans = [0]; // start from 0
  for (let i = 1; i <= n; i++) {
    const m = Math.pow(2, i - 1);
    for (let j = ans.length - 1; j >= 0; j--) {
      ans.push(m + ans[j]);
    }
  }
  return ans;
}
```

```js
let make = (n) => {
  let result = []
  if (n === 1) {
    return [0, 1]
  } else {
    let prev = make(n - 1)
    let max = Math.pow(2, n) - 1
    for (let index = 0; index < prev.length; index++) {
      result[index] = `0${prev[index]}`
      result[max - index] = `1${prev[index]}`
    }
  }
  return result
}
let result = make(n)
return result.map(item => {
  return parseInt(item, 2)
})
```