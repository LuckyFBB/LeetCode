<!--
 * @Author: FBB
 * @Date: 2020-04-13 21:28:33
 * @LastEditors: FBB
 * @LastEditTime: 2020-04-13 21:30:57
 * @Description:
 -->

> 原文链接

[https://leetcode.com/problems/last-stone-weight/](https://leetcode.com/problems/last-stone-weight/)

> 题目内容

We have a collection of stones, each stone has a positive integer weight.

Each turn, we choose the two heaviest stones and smash them together. Suppose the stones have weights x and y with x <= y. The result of this smash is:

- If x == y, both stones are totally destroyed;
- If x != y, the stone of weight x is totally destroyed, and the stone of weight y has new weight y-x.
  At the end, there is at most 1 stone left. Return the weight of this stone (or 0 if there are no stones left.)

**Example 1:**

```
Input: [2,7,4,1,8,1]
Output: 1
Explanation:
We combine 7 and 8 to get 1 so the array converts to [2,4,1,1,1] then,
we combine 2 and 4 to get 2 so the array converts to [2,1,1,1] then,
we combine 2 and 1 to get 1 so the array converts to [1,1,1] then,
we combine 1 and 1 to get 0 so the array converts to [1] then that's the value of last stone.
```

**Note:**

1. 1 <= stones.length <= 30
2. 1 <= stones[i] <= 1000

> 解题思路

- 思路 1
  使用 sort 和 pop 拿到最大的两个值

```js
/**
 * @param {number[]} stones
 * @return {number}
 */
var lastStoneWeight = function (stones) {
  if (stones.length === 1) {
    return stones[0];
  }
  if (stones.length === 2) {
    return Math.abs(stones[0] - stones[1]);
  }
  while (stones.length > 1) {
    stones.sort((a, b) => a - b);
    let y = stones.pop();
    let x = stones.pop();
    if (y > x) stones.unshift(y - x);
  }
  return stones.length ? stones[0] : 0;
};
```
