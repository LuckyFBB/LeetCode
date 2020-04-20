<!--
 * @Author: FBB
 * @Date: 2020-04-20 15:00:52
 * @LastEditors: FBB
 * @LastEditTime: 2020-04-20 17:26:20
 * @Description:
 -->

> 原文链接

[https://leetcode.com/problems/same-tree/](https://leetcode.com/problems/same-tree/)

> 题目内容

Given a binary tree, check whether it is a mirror of itself (ie, symmetric around its center).

For example, this binary tree [1,2,2,3,4,4,3] is symmetric:

```
    1
   / \
  2   2
 / \ / \
3  4 4  3
```

But the following [1,2,2,null,3,null,3] is not:

```
    1
   / \
  2   2
   \   \
   3    3
```

**Follow up:** Solve it both recursively and iteratively.

> 解题思路

- 思路 1
  按着二叉树的递归三原则
  1. 找到结束条件：root 为 null
  2. 找到要返回的值：是否为true
  3. 在此递归中需要做什么：判断当前两个比较的值是否相同

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
 * @return {boolean}
 */
var isSymmetric = function (root) {
  const traverse = (q, p) => {
    if (q === null && p === null) return true;
    if (!q || !p) return false;
    if (q.val !== p.val) return false;
    return traverse(q.left, p.right) && traverse(q.right, p.left);
  };
  if (!root) return true;
  return traverse(root.left, root.right);
};
```
