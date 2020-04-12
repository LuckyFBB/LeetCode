<!--
 * @Author: FBB
 * @Date: 2020-04-12 11:00:46
 * @LastEditors: FBB
 * @LastEditTime: 2020-04-12 11:03:04
 * @Description:
 -->

> 原文链接

[https://leetcode.com/problems/diameter-of-binary-tree/](https://leetcode.com/problems/diameter-of-binary-tree/)

> 题目内容

Given a binary tree, you need to compute the length of the diameter of the tree. The diameter of a binary tree is the length of the **longest** path between any two nodes in a tree. This path may or may not pass through the root.

**Example:**
```
Given a binary tree
    1
   / \
  2   3
 / \  
4   5  
```
Return 3, which is the length of the path [4,2,1,3] or [5,2,1,3].

**Note:** The length of path between two nodes is represented by the number of edges between them.

> 解题思路

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
var diameterOfBinaryTree = function (root) {
  let max = 0;

  var getHeight = function (root) {
    if (root === null) return 0;
    var right = getHeight(root.right);
    let left = getHeight(root.left);
    max = Math.max(max, left + right);
    return Math.max(left, right) + 1;
  };

  getHeight(root);
  return max;
};
```
