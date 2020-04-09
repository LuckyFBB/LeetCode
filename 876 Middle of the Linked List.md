<!--
 * @Author: FBB
 * @Date: 2020-04-08 22:37:25
 * @LastEditors: FBB
 * @LastEditTime: 2020-04-09 21:32:34
 * @Description:
 -->

> 原文链接

[https://leetcode.com/problems/middle-of-the-linked-list/](https://leetcode.com/problems/middle-of-the-linked-list/)

> 题目内容

Given a non-empty, singly linked list with head node head, return a middle node of linked list.

If there are two middle nodes, return the second middle node.

**Example 1:**

Input: [1,2,3,4,5]
Output: Node 3 from this list (Serialization: [3,4,5])
The returned node has value 3. (The judge's serialization of this node is [3,4,5]).
Note that we returned a ListNode object ans, such that:
ans.val = 3, ans.next.val = 4, ans.next.next.val = 5, and ans.next.next.next = NULL.
**Example 2:**

Input: [1,2,3,4,5,6]
Output: Node 4 from this list (Serialization: [4,5,6])
Since the list has two middle nodes with values 3 and 4, we return the second one.

**Note:**

- The number of nodes in the given list will be between 1 and 100.

> 解题思路

- 思路 1
  先获取到链表的 length，然后再拿到 length/2 时的 node

```js
/**
 * Definition for singly-linked list.
 * function ListNode(val) {
 *     this.val = val;
 *     this.next = null;
 * }
 */
/**
 * @param {ListNode} head
 * @return {ListNode}
 */
var middleNode = function (head) {
  let targetLength = Math.ceil(getLength(head) / 2);
  return getMiddleNode(head, targetLength);
};

var getLength = function (node) {
  let length = 0;
  while (node.next) {
    length += 1;
    node = node.next;
  }
  return length;
};
var getMiddleNode = function (node, targetLength) {
  for (let i = 0; i < targetLength; i++) {
    node = node.next;
  }
  return node;
};
```
