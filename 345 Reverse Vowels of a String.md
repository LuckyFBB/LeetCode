> 原文链接

[https://leetcode.com/problems/reverse-vowels-of-a-string/](https://leetcode.com/problems/reverse-vowels-of-a-string/)
> 题目内容

Write a function that takes a string as input and reverse only the vowels of a string.

**Example 1**:
```
Input: "hello"
Output: "holle"
```
**Example 2**:
```
Input: "leetcode"
Output: "leotcede"
```
**Note**:
The vowels does not include the letter "y".

> 解题思路

```js
/**
* @param {string} s
* @return {string}
*/
var reverseVowels = function (s) {
  let vowelSet = new Set(['a', 'e', 'i', 'o', 'u', 'A', 'E', 'I', 'O', 'U']);
  let left = 0;
  let right = s.length - 1;
  s = s.split('')
  while (left < right) {
    while (!vowelSet.has(s[left]) && left < s.length) left++
    while (!vowelSet.has(s[right]) && right > 0) right--
    if (left < right) {
      swap(s, left, right)
      left++
      right--
    }
  }
  return s.join('')
};

function swap(arr, i, j) {
  let temp = arr[i];
  arr[i] = arr[j];
  arr[j] = temp;
}
```