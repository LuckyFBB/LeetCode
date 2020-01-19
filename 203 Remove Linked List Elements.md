> 原文链接

[https://leetcode.com/problems/remove-linked-list-elements/](https://leetcode.com/problems/remove-linked-list-elements/)

> 题目内容

Remove all elements from a linked list of integers that have value val.

**Example:**

Input: 1->2->6->3->4->5->6, val = 6
Output: 1->2->3->4->5

> 解题思路

```js
/**
 * @param {ListNode} head
 * @param {number} val
 * @return {ListNode}
 */
var removeElements = function(head, val) {
  if (head === null) {
    return head;
  }
  while (head !== null && head.val === val) {
    head = head.next;
  }
  var pre = head;
  while (pre !== null && pre.next !== null) {
    var cur = pre.next;
    if (cur.val !== val) {
      pre = cur;
      continue;
    }
    pre.next = cur.next;
  }

  return head;
};
```
