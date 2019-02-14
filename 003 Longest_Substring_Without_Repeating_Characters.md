> 原文链接

[https://leetcode.com/problems/longest-substring-without-repeating-characters/](https://leetcode.com/problems/longest-substring-without-repeating-characters/)
> 题目内容

Given a string, find the length of the longest substring without repeating characters.

Example 1:
```
Input: "abcabcbb"
Output: 3 
Explanation: The answer is "abc", with the length of 3. 
```
Example 2:
```
Input: "bbbbb"
Output: 1
Explanation: The answer is "b", with the length of 1.
```
Example 3:
```
Input: "pwwkew"
Output: 3
Explanation: The answer is "wke", with the length of 3. 
             Note that the answer must be a substring, "pwke" is a subsequence and not a substring.
```
> 解题思路

使用冒泡排序和Set数据结构。时间复杂度O(N^2)

```js
/**
 * @param {string} s
 * @return {number}
 */
var lengthOfLongestSubstring = function (s) {
  let result = 0;
  for (let i = 0; i < s.length; i++) {
    let set = new Set();
    set.add(s.charAt(i));
    for (let j = i + 1; j < s.length; j++) {
      if (set.has(s.charAt(j))) {    //判断是否含有该数据
        break;
      }
      else set.add(s.charAt(j));
    }
    result = Math.max(result, set.size)   //比较当前结果和新的size
  }
  return result;
};
```