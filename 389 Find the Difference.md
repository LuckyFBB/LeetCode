> 原文链接

[https://leetcode.com/problems/find-the-difference/](https://leetcode.com/problems/find-the-difference/)

> 题目内容

Given two strings s and t which consist of only lowercase letters.

String t is generated by random shuffling string s and then add one more letter at a random position.

Find the letter that was added in t.

**Example:**

```
Input:
s = "abcd"
t = "abcde"

Output:
e

Explanation:
'e' is the letter that was added.
```

> 解题思路

```js
/**
 * @param {string} s
 * @param {string} t
 * @return {character}
 */
var findTheDifference = function(s, t) {
  for (let i = 0; i < s.length; i++) {
    const element = s[i];
    t = t.replace(element, "");
  }
  return t;
};
```