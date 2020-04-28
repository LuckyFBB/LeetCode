<!--
 * @Author: FBB
 * @Date: 2020-04-28 20:00:58
 * @LastEditors: FBB
 * @LastEditTime: 2020-04-28 20:02:15
 * @Description:
 -->

[https://leetcode.com/problems/implement-stack-using-queues/](https://leetcode.com/problems/implement-stack-using-queues/)

> 题目内容

Implement the following operations of a stack using queues.

- push(x) -- Push element x onto stack.
- pop() -- Removes the element on top of the stack.
- top() -- Get the top element.
- empty() -- Return whether the stack is empty.

**Example:**

```
MyStack stack = new MyStack();

stack.push(1);
stack.push(2);
stack.top();   // returns 2
stack.pop();   // returns 2
stack.empty(); // returns false
```

**Notes:**

- You must use only standard operations of a queue -- which means only push to back, peek/pop from front, size, and is empty operations are valid.
- Depending on your language, queue may not be supported natively. You may simulate a queue by using a list or deque (double-ended queue), as long as you use only standard operations of a queue.
- You may assume that all operations are valid (for example, no pop or top operations will be called on an empty stack).

> 解题思路

```js
/**
 * Initialize your data structure here.
 */
var MyStack = function () {
  this.queue = [];
};

/**
 * Push element x onto stack.
 * @param {number} x
 * @return {void}
 */
MyStack.prototype.push = function (x) {
  this.queue.push(x);
};

/**
 * Removes the element on top of the stack and returns that element.
 * @return {number}
 */
MyStack.prototype.pop = function () {
  let index = 0;
  while (index < this.queue.length - 1) {
    const element = this.queue.shift();
    this.queue.push(element);
    index++;
  }
  return this.queue.shift();
};

/**
 * Get the top element.
 * @return {number}
 */
MyStack.prototype.top = function () {
  let index = 0;
  while (index < this.queue.length - 1) {
    const element = this.queue.shift();
    this.queue.push(element);
    index++;
  }
  const top = this.queue.shift();
  this.queue.push(top);
  return top;
};

/**
 * Returns whether the stack is empty.
 * @return {boolean}
 */
MyStack.prototype.empty = function () {
  return !this.queue.length;
};

/** 
 * Your MyStack object will be instantiated and called as such:
 * var obj = new MyStack()
 * obj.push(x)
 * var param_2 = obj.pop()
 * var param_3 = obj.top()
 * var param_4 = obj.empty()
 */
```
