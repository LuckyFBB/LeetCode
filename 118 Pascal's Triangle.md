> 原文链接

[https://leetcode.com/problems/pascals-triangle/](https://leetcode.com/problems/pascals-triangle/)

> 题目内容

Given a non-negative integer numRows, generate the first numRows of Pascal's triangle.

In Pascal's triangle, each number is the sum of the two numbers directly above it.
![](https://upload.wikimedia.org/wikipedia/commons/0/0d/PascalTriangleAnimated2.gif)

**Example:**

```
Input: 5
Output:
[
     [1],
    [1,1],
   [1,2,1],
  [1,3,3,1],
 [1,4,6,4,1]
]
```

> 解题思路

```js
/**
 * @param {number} numRows
 * @return {number[][]}
 */
var generate = function(numRows) {
  let result = [];
  if (numRows < 1) {
    return result;
  }
  result.push([1]);
  if (numRows === 1) {
    return result;
  }
  result.push([1, 1]);
  for (let i = 3; i <= numRows; i++) {
    let last = result[i - 2];
    let temp = [];
    temp.push(1);
    for (let k = 1, j = 0; k < i - 1; k++) {
      temp.push(last[j] + last[k]);
      j++;
    }
    temp.push(1);
    result.push(temp);
  }
  return result;
};
```
