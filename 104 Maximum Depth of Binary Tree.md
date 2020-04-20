<!--
 * @Author: FBB
 * @Date: 2020-04-20 17:34:05
 * @LastEditors: FBB
 * @LastEditTime: 2020-04-20 17:35:19
 * @Description:
 -->

> 原文链接

[https://leetcode.com/problems/maximum-depth-of-binary-tree/](https://leetcode.com/problems/maximum-depth-of-binary-tree/)

> 题目内容

Given a binary tree, find its maximum depth.

The maximum depth is the number of nodes along the longest path from the root node down to the farthest leaf node.

**Note:** A leaf is a node with no children.

**Example:**

```
Given binary tree [3,9,20,null,null,15,7],

    3
   / \
  9  20
    /  \
   15   7
```

return its depth = 3.

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
 * @return {number}
 */
var maxDepth = function (root) {
  if (!root) return 0;
  let lefth = maxDepth(root.left);
  let righth = maxDepth(root.right);
  return Math.max(lefth, righth) + 1;
};
```
