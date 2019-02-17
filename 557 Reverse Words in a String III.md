> 原文链接

[https://leetcode.com/problems/reverse-words-in-a-string-iii/](https://leetcode.com/problems/reverse-words-in-a-string-iii/)
> 题目内容

Given a string, you need to reverse the order of characters in each word within a sentence while still preserving whitespace and initial word order.

**Example 1:**  
```w
Input: "Let's take LeetCode contest"  
Output: "s'teL ekat edoCteeL tsetnoc"
```

**Note:** In the string, each word is separated by single space and there will not be any extra space in the string.

> 解题思路

```js
/**
 * @param {string} s
 * @return {string}
 */
var reverseWords = function(s) {
  let words = s.split(' ')
  let result = words.map(item => {
    return item.split('').reverse().join('')
  })
  return result.join(' ')
};
```