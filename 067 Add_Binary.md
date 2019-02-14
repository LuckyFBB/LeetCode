> 原文链接

[https://leetcode.com/problems/add-binary/](https://leetcode.com/problems/add-binary/)
> 题目内容

Given two binary strings, return their sum (also a binary string).

The input strings are both non-empty and contains only characters 1 or 0.

Example 1:
```t
Input: a = "11", b = "1"
Output: "100"
```
Example 2:
```t
Input: a = "1010", b = "1011"
Output: "10101"
```

> 解题思路

对于每一位数进行加法，如有进位单独计算

时间复杂度O(N)

```js
/**
 * @param {string} a
 * @param {string} b
 * @return {string}
 */
var addBinary = function(a, b) {
  let result = '';
  let lenA = a.length-1;
  let lenB = b.length-1;
  let mod = 0;
  let carry = 0;
  while(lenA>=0||lenB>=0){
    let aDig = a[lenA]||0;
    let bDig = b[lenB]||0;
    let temp = parseInt(aDig) + parseInt(bDig) + carry;
    mod = temp % 2;
    carry = Math.floor(temp/2);
    result = mod + result;
    lenA--;
    lenB--;
  }
  if(carry!==0) result=carry+result;
  return result;
};
```