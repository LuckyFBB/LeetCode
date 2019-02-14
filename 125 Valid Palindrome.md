> 原文链接

[https://leetcode.com/problems/valid-palindrome/](https://leetcode.com/problems/valid-palindrome/)
> 题目内容

Given a string, determine if it is a palindrome, considering only alphanumeric characters and ignoring cases.

Note: For the purpose of this problem, we define empty string as valid palindrome.

**Example 1**:
```
Input: "A man, a plan, a canal: Panama"
Output: true
```
**Example 2**:
```
Input: "race a car"
Output: false
```

> 解题思路

```js
/**
* @param {string} s
* @return {boolean}
*/
var isPalindrome = function (s) {
  s = s.replace(/[^\w]/g, '').toLowerCase();
  let j = s.length - 1;
  for (let i = 0; i < s.length / 2; i++) {
    if (s[i] != s[j]) {
      return false;
    }
    j--;
  }
  return true;
  };
```