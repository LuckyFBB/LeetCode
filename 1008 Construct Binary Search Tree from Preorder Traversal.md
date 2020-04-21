<!--
 * @Author: FBB
 * @Date: 2020-04-21 21:04:33
 * @LastEditors: FBB
 * @LastEditTime: 2020-04-21 21:06:51
 * @Description: 
 -->

> 原文链接

[https://leetcode.com/problems/construct-binary-search-tree-from-preorder-traversal/](https://leetcode.com/problems/construct-binary-search-tree-from-preorder-traversal/)

> 题目内容

Return the root node of a binary search tree that matches the given preorder traversal.

(Recall that a binary search tree is a binary tree where for every node, any descendant of node.left has a value < node.val, and any descendant of node.right has a value > node.val.  Also recall that a preorder traversal displays the value of the node first, then traverses node.left, then traverses node.right.)

**Example 1:**
```
Input: [8,5,1,7,10,12]
Output: [8,5,10,1,7,null,12]
```

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
 * @param {number[]} preorder
 * @return {TreeNode}
 */
var bstFromPreorder = function (preorder) {
  let tree = new TreeNode(preorder[0]);
  preorder.slice(1).forEach((item) => {
    _insertNode(tree, item);
  });
  return tree;
};
function _insertNode(node, key) {
  if (node.val > key) {
    //插入左子树
    node.left ? _insertNode(node.left, key) : (node.left = new TreeNode(key));
  } else {
    node.right
      ? _insertNode(node.right, key)
      : (node.right = new TreeNode(key));
  }
}
```
