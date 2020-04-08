<!--
 * @Author: FBB
 * @Date: 2020-04-08 21:45:16
 * @LastEditors: FBB
 * @LastEditTime: 2020-04-08 21:58:46
 * @Description:
 -->

> 原文链接

[https://leetcode.com/problems/group-anagrams/](https://leetcode.com/problems/group-anagrams/)

> 题目内容

Given an array of strings, group anagrams together.

**Example:**

```
Input: ["eat", "tea", "tan", "ate", "nat", "bat"],
Output:
[
  ["ate","eat","tea"],
  ["nat","tan"],
  ["bat"]
]
```

**Note:**

- All inputs will be in lowercase.
- The order of your output does not matter.

> 解题思路

思路 1：由于只有小学字母，所以只要对每个单词进行一个排序，然后进行分类，即可实现。

```js
/**
 * @param {string[]} strs
 * @return {string[][]}
 */
var groupAnagrams = function (strs) {
  const map = {};
  for (let str of strs) {
    const sorted = str.split("").sort().join("");
    map[sorted] ? map[sorted].push(str) : (map[sorted] = [str]);
  }
  return Object.values(map);
};
```
