> 原文链接

[https://leetcode.com/problems/roman-to-integer/](https://leetcode.com/problems/roman-to-integer/)
> 题目内容

Write a function to find the longest common prefix string amongst an array of strings.

If there is no common prefix, return an empty string "".

Example 1:
```
Input: ["flower","flow","flight"]
Output: "fl"
```
Example 2:
```
Input: ["dog","racecar","car"]
Output: ""
Explanation: There is no common prefix among the input strings.
```
Note:
All given inputs are in lowercase letters a-z.

> 解题思路

循环遍历数组
循环查找数组第一个元素

时间复杂度O(N^2)

```js
/**
 * @param {string[]} strs
 * @return {string}
 */
var longestCommonPrefix = function (strs) {
  let prefix = (strs.length) ? strs[0] : '';
  let i = 1;
  while (i < strs.length) {
    let curr = strs[i];
    while (curr.indexOf(prefix) !== 0) {
      prefix = prefix.slice(0, -1);
    }
    i++;
  }
  return prefix;
};
```