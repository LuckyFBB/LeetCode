> 原文链接

[https://leetcode.com/problems/fizz-buzz/](https://leetcode.com/problems/fizz-buzz/)

> 题目内容

Write a program that outputs the string representation of numbers from 1 to n.

But for multiples of three it should output “Fizz” instead of the number and for the multiples of five output “Buzz”. For numbers which are multiples of both three and five output “FizzBuzz”.

**Example:**

```
n = 15,

Return:
[
    "1",
    "2",
    "Fizz",
    "4",
    "Buzz",
    "Fizz",
    "7",
    "8",
    "Fizz",
    "Buzz",
    "11",
    "Fizz",
    "13",
    "14",
    "FizzBuzz"
]
```

> 解题思路

思路 1：ES6 解构赋值

```js
/**
 * @param {number} n
 * @return {string[]}
 */
var fizzBuzz = function(n) {
  let result = [];
  for (let i = 0; i < n; i++) {
    if ((i + 1) % 15 === 0) {
      result.push("FizzBuzz");
    } else if ((i + 1) % 3 === 0) {
      result.push("Fizz");
    } else if ((i + 1) % 5 === 0) {
      result.push("Buzz");
    } else {
      result.push(`${i + 1}`);
    }
  }
  return result;
};
```
