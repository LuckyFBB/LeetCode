<!--
 * @Author: FBB
 * @Date: 2020-04-20 15:52:06
 * @LastEditors: FBB
 * @LastEditTime: 2020-04-20 16:02:38
 * @Description:
 -->

> 原文链接

[https://leetcode.com/problems/range-sum-of-bst/](https://leetcode.com/problems/range-sum-of-bst/)

> 题目内容

Given the root node of a binary search tree, return the sum of values of all nodes with value between L and R (inclusive).

The binary search tree is guaranteed to have unique values.

**Example 1:**

```
Input: root = [10,5,15,3,7,null,18], L = 7, R = 15
Output: 32
```

**Example 2:**

```
Input: root = [10,5,15,3,7,13,18,1,null,6], L = 6, R = 10
Output: 23
```

**Note:**

The number of nodes in the tree is at most 10000.
The final answer is guaranteed to be less than 2^31.

> 解题思路

- 思路 1
  按着二叉树的递归三原则
  1. 找到结束条件：root 为 null
  2. 找到要返回的值：sum
  3. 在此递归中需要做什么：L< val < R 时，sum+=val

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
 * @param {number} L
 * @param {number} R
 * @return {number}
 */
var rangeSumBST = function (root, L, R) {
  const sum = 0;
  if (!root) return sum;
  const { val, left, right } = root;
  return (
    (val >= L && val <= R ? sum + val : sum) +
    (val > L ? rangeSumBST(left, L, R) : 0) +
    (val < R ? rangeSumBST(right, L, R) : 0)
  );
};
```
