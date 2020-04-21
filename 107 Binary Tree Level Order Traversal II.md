<!--
 * @Author: FBB
 * @Date: 2020-04-21 21:09:55
 * @LastEditors: FBB
 * @LastEditTime: 2020-04-21 21:15:04
 * @Description:
 -->

> 原文链接

[https://leetcode.com/problems/binary-tree-level-order-traversal-ii/](https://leetcode.com/problems/binary-tree-level-order-traversal-ii/)

> 题目内容

Given a binary tree, return the bottom-up level order traversal of its nodes' values. (ie, from left to right, level by level from leaf to root).

**For example:**
Given binary tree [3,9,20,null,null,15,7],

```
    3
   / \
  9  20
    /  \
   15   7
```

return its bottom-up level order traversal as:

```
[
  [15,7],
  [9,20],
  [3]
]
```

> 解题思路

- 思路 1
  按着二叉树的递归三原则

```js
/**
 * Definition for a binary tree node.
 * function TreeNode(val) {
 *     this.val = val;
 *     this.left = this.right = null;
 * }
 */
/**
 * @param {TreeNode} root
 * @return {number[][]}
 */
var levelOrderBottom = function (root) {
  let result = [];
  const traverse = (node, depth) => {
    if (!node) return;
    result[depth] ? result[depth].push(node.val) : (result[depth] = [node.val]);
    node.left && traverse(node.left, depth + 1);
    node.right && traverse(node.right, depth + 1);
  };
  traverse(root, 0);
  return result.reverse();
};
```
