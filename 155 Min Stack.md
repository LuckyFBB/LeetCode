> 原文链接

[https://leetcode.com/problems/min-stack/](https://leetcode.com/problems/min-stack/)

> 题目内容

Design a stack that supports push, pop, top, and retrieving the minimum element in constant time.

- push(x) -- Push element x onto stack.
- pop() -- Removes the element on top of the stack.
- top() -- Get the top element.
- getMin() -- Retrieve the minimum element in the stack.

**Example:**

```
MinStack minStack = new MinStack();
minStack.push(-2);
minStack.push(0);
minStack.push(-3);
minStack.getMin();   --> Returns -3.
minStack.pop();
minStack.top();      --> Returns 0.
minStack.getMin();   --> Returns -2.
```

> 解题思路

- 思路：数组模拟栈

```js
var MinStack = function() {
  this.stack = [];
};

/**
 * @param {number} x
 * @returns {void}
 */
MinStack.prototype.push = function(x) {
  this.stack.push(x);
};

/**
 * @returns {void}
 */
MinStack.prototype.pop = function() {
  this.stack.pop();
};

/**
 * @returns {number}
 */
MinStack.prototype.top = function() {
  return this.stack[this.stack.length - 1];
};

/**
 * @returns {number}
 */
MinStack.prototype.getMin = function() {
  return Math.min.apply(null, this.stack);
};
```
