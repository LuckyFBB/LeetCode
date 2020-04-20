<!--
 * @Author: FBB
 * @Date: 2020-04-20 20:37:19
 * @LastEditors: FBB
 * @LastEditTime: 2020-04-20 20:38:36
 * @Description:
 -->

> 原文链接

[https://leetcode.com/problems/binary-tree-inorder-traversal/](https://leetcode.com/problems/binary-tree-inorder-traversal/)

> 题目内容

Given a binary tree, return the inorder traversal of its nodes' values.

**Example:**

```
Input: [1,null,2,3]
   1
    \
     2
    /
   3

Output: [1,3,2]
```

**Follow up:** Recursive solution is trivial, could you do it iteratively?

> 解题思路

- 思路 1
  中序遍历

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
 * @return {number[]}
 */
var inorderTraversal = function (root) {
  const output = [];
  const traverse = (node) => {
    if (!node) return output;
    node.left && traverse(node.left);
    output.push(node.val);
    node.right && traverse(node.right);
    return output;
  };
  return traverse(root);
};
```
