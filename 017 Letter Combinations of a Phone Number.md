> 原文链接

[https://leetcode.com/problems/letter-combinations-of-a-phone-number/](https://leetcode.com/problems/letter-combinations-of-a-phone-number/)

> 题目内容

Given a string containing digits from 2-9 inclusive, return all possible letter combinations that the number could represent.

A mapping of digit to letters (just like on the telephone buttons) is given below. Note that 1 does not map to any letters.

**Example:**
```
Input: "23"
Output: ["ad", "ae", "af", "bd", "be", "bf", "cd", "ce", "cf"].
```
**Note:**

Although the above answer is in lexicographical order, your answer could be in any order you want.

> 解题思路


```js
/**
 * @param {string} digits
 * @return {string[]}
 */
//测试能够通过，但是不能提交成功，runtimeError
let map = ['',1,'abc','def','ghi','jkl','mno','pqrs','tuv','wxyz']

var letterCombinations = function(digits) {
  let num = digits.split('')
  let code = num.map(item => {
    return map[item]
  })
  return comb(code)
};

let comb = (arr) => {
  let temp = []
  let firstL = arr[0].length
  let secondL = arr[1].length
  for (let i = 0; i < firstL; i++) {
    for (let j = 0; j < secondL; j++) {
      temp.push(`${arr[0][i]}${arr[1][j]}`)
    }
  }
  arr.splice(0, 2, temp)
  if (arr.length > 1) {
    comb(arr)
  } else {
    return temp
  }
  return arr[0]
}
```

```js
/**
 * @param {string} digits
 * @return {string[]}
 */
var letterCombinations = function (digits) {
  if (digits === "") {
    return []
  }
  let map = new Map()
  map.set("2", ['a', 'b', 'c'])
  map.set("3", ['d', 'e', 'f'])
  map.set("4", ['g', 'h', 'i'])
  map.set("5", ['j', 'k', 'l'])
  map.set("6", ['m', 'n', 'o'])
  map.set("7", ['p', 'q', 'r', 's'])
  map.set("8", ['t', 'u', 'v'])
  map.set("9", ['w', 'x', 'y', 'z'])

  let num = digits.split('')
  let code = num.map(item => {
    return map.get(item)
  })
  let res = code.reduce(function (prev, curr) {
    let temp = []
    prev.forEach(prevItem => {
      curr.forEach(currItem => {
        temp.push(`${prevItem}${currItem}`)
      })
    })
    return temp
  })
  return res
}
```