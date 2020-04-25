<!--
 * @Author: FBB
 * @Date: 2020-04-25 16:50:15
 * @LastEditors: FBB
 * @LastEditTime: 2020-04-25 16:56:39
 * @Description:
 -->

> 原文链接

[https://leetcode.com/problems/linked-list-cycle/](https://leetcode.com/problems/linked-list-cycle/)

> 题目内容

Given a linked list, return the node where the cycle begins. If there is no cycle, return null.

To represent a cycle in the given linked list, we use an integer pos which represents the position (0-indexed) in the linked list where tail connects to. If pos is -1, then there is no cycle in the linked list.

**Note:** Do not modify the linked list.

**Example 1:**

```
Input: head = [3,2,0,-4], pos = 1
Output: tail connects to node index 1
Explanation: There is a cycle in the linked list, where tail connects to the second node.
```

![](https://assets.leetcode.com/uploads/2018/12/07/circularlinkedlist.png)
**Example 2:**

```
Input: head = [1,2], pos = 0
Output: tail connects to node index 0
Explanation: There is a cycle in the linked list, where tail connects to the first node.
```

![](https://assets.leetcode.com/uploads/2018/12/07/circularlinkedlist_test2.png)

**Example 3:**

```
Input: head = [1], pos = -1
Output: no cycle
Explanation: There is no cycle in the linked list.
```

![](https://assets.leetcode.com/uploads/2018/12/07/circularlinkedlist_test3.png)

**Follow-up:**
Can you solve it without using extra space?

> 解题思路

- 思路 1
  [参考](https://www.cnblogs.com/hiddenfox/p/3408931.html)

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
var detectCycle = function (head) {
  let fast = head;
  let slow = head;
  while (fast && fast.next && fast.next.next) {
    fast = fast.next.next;
    slow = slow.next;
    if (slow === fast) {
      slow = head;
      while (slow !== fast) {
        slow = slow.next;
        fast = fast.next;
      }
      return slow;
    }
  }
  return null;
};
```
