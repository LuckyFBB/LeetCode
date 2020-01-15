> 原文链接

[https://leetcode.com/problems/pascals-triangle-ii](https://leetcode.com/problems/pascals-triangle-ii)

> 题目内容

Given a non-negative index k where k ≤ 33, return the kth index row of the Pascal's triangle.

Note that the row index starts from 0.

In Pascal's triangle, each number is the sum of the two numbers directly above it.
![](https://upload.wikimedia.org/wikipedia/commons/0/0d/PascalTriangleAnimated2.gif)

**Example:**

```
Input: 3
Output: [1,3,3,1]
```

**Follow up:**
Could you optimize your algorithm to use only O(k) extra space?

> 解题思路

```js
/**
 * @param {number} rowIndex
 * @return {number[]}
 */
var getRow = function(rowIndex) {
  if (rowIndex === 0) {
    return [1];
  }
  if (rowIndex > 0) {
    let result = [1];
    const prev = getRow(rowIndex - 1);
    for (let i = 0; i < rowIndex - 1; i++) {
      result.push(prev[i] + prev[i + 1]);
    }
    result.push(1);
    return result;
  }
};
```
