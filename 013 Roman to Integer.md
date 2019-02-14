> 原文链接

[https://leetcode.com/problems/roman-to-integer/](https://leetcode.com/problems/roman-to-integer/)
> 题目内容

Roman numerals are represented by seven different symbols: I, V, X, L, C, D and M.
```t
Symbol       Value
I             1
V             5
X             10
L             50
C             100
D             500
M             1000
```
For example, two is written as II in Roman numeral, just two one's added together. Twelve is written as, XII, which is simply X + II. The number twenty seven is written as XXVII, which is XX + V + II.

Roman numerals are usually written largest to smallest from left to right. However, the numeral for four is not IIII. Instead, the number four is written as IV. Because the one is before the five we subtract it making four. The same principle applies to the number nine, which is written as IX. There are six instances where subtraction is used:

- I can be placed before V (5) and X (10) to make 4 and 9. 
- X can be placed before L (50) and C (100) to make 40 and 90. 
- C can be placed before D (500) and M (1000) to make 400 and 900.
Given a roman numeral, convert it to an integer. Input is guaranteed to be within the range from 1 to 3999.

Example 1:
```t
Input: "III"
Output: 3
```
Example 2:
```t
Input: "IV"
Output: 4
```
Example 3:
```t
Input: "IX"
Output: 9
```
Example 4:
```t
Input: "LVIII"
Output: 58
Explanation: L = 50, V= 5, III = 3.
```
Example 5:
```t
Input: "MCMXCIV"
Output: 1994
Explanation: M = 1000, CM = 900, XC = 90 and IV = 4.
```

> 解题思路

利用对象，读取到每一个字符的数字，判断后者代表的数字是否大于前者

时间复杂度O(N)

```js
/**
 * @param {string} s
 * @return {number}
 */
let roman = {
  'I': 1,
  'V': 5,
  'X': 10,
  'L': 50,
  'C': 100,
  'D': 500,
  'M': 1000
}
var romanToInt = function (s) {
  let result = 0;
  for (let i = 0; i < s.length; i++) {
    let curr = s[i];
    let next = s[i + 1];
    if (roman[curr] < roman[next]) {
      let temp = roman[next] - roman[curr];
      result += temp;
      i++;
    } else {
      result += roman[curr];
    }
  }
  return result;
};
```