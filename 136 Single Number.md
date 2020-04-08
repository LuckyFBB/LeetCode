> 原文链接

[https://leetcode.com/problems/single-number/](https://leetcode.com/problems/single-number/)

> 题目内容

GGiven a non-empty array of integers, every element appears twice except for one. Find that single one.

**Note:**

Your algorithm should have a linear runtime complexity. Could you implement it without using extra memory?

**Example 1:**

```
Input: [2,2,1]
Output: 1
```

**Example 2:**

```
Input: [4,1,2,1,2]
Output: 4
```

> 解题思路

- 思路一
  基础实现方式，算法复杂度为 O(n^2)

```js
/**
 * @param {number[]} nums
 * @return {number}
 */
var singleNumber = function (nums) {
  let number = [nums[0]];
  for (let i = 1; i < nums.length; i++) {
    let index = number.indexOf(nums[i]);
    index === -1 ? number.push(nums[i]) : number.splice(index, 1);
  }
  return number[0];
};
```

- 思路二
  使用对象统计数组数据个数来完成

```js
/**
 * @param {number[]} nums
 * @return {number}
 */
var singleNumber = function (nums) {
  const map = {};
  nums.forEach((_) => (map[_] ? map[_]++ : (map[_] = 1)));
  for (let n in map) {
    if (map[n] === 1) return Number(n);
  }
};
```

- 思路三
  因为数组中的数据，除了某个元素之外都是出现两次的。在逻辑运算中，异或操作能够很好的处理相同的数据。关于[异或](https://baike.baidu.com/item/%E5%BC%82%E6%88%96)操作，百度百科的解释。

```js
const singleNumber = (nums) => {
  let ret = 0;
  for (const n of nums) ret ^= n;
  return ret;
};
```
