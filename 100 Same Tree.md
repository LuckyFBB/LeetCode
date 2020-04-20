<!--
 * @Author: FBB
 * @Date: 2020-04-20 15:00:52
 * @LastEditors: FBB
 * @LastEditTime: 2020-04-20 15:52:40
 * @Description:
 -->

> 原文链接

[https://leetcode.com/problems/same-tree/](https://leetcode.com/problems/same-tree/)

> 题目内容

Given two binary trees, write a function to check if they are the same or not.

Two binary trees are considered the same if they are structurally identical and the nodes have the same value.

**Example 1:**

```
Input:     1         1
          / \       / \
         2   3     2   3

        [1,2,3],   [1,2,3]

Output: true
```

**Example 2:**

```
Input:     1         1
          /           \
         2             2

        [1,2],     [1,null,2]

Output: false
```

**Example 3:**

```
Input:     1         1
          / \       / \
         2   1     1   2

        [1,2,1],   [1,1,2]

Output: false
```

> 解题思路

- 思路 1
  采用递归

```js
/**
 * @param {TreeNode} p
 * @param {TreeNode} q
 * @return {boolean}
 */
var isSameTree = function (p, q) {
  if (p === null && q === null) return true;
  if (!p || !q) return false;
  if (p.val !== q.val) return false;
  return isSameTree(p.right, q.right) && isSameTree(p.left, q.left);
};
```
