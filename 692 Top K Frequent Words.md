<!--
 * @Author: FBB
 * @Date: 2020-05-09 14:56:55
 * @LastEditors: FBB
 * @LastEditTime: 2020-05-09 15:01:05
 * @Description: 
 -->
> 原文链接

[https://leetcode.com/problems/top-k-frequent-words/](https://leetcode.com/problems/top-k-frequent-words/)

> 题目内容

Given a non-empty list of words, return the k most frequent elements.

Your answer should be sorted by frequency from highest to lowest. If two words have the same frequency, then the word with the lower alphabetical order comes first.

**Example 1:**
```
Input: ["i", "love", "leetcode", "i", "love", "coding"], k = 2
Output: ["i", "love"]
Explanation: "i" and "love" are the two most frequent words.
    Note that "i" comes before "love" due to a lower alphabetical order.
```

**Example 2:**
```
Input: ["the", "day", "is", "sunny", "the", "the", "the", "sunny", "is", "is"], k = 4
Output: ["the", "is", "sunny", "day"]
Explanation: "the", "is", "sunny" and "day" are the four most frequent words,
    with the number of occurrence being 4, 3, 2 and 1 respectively.
```

**Note:**
You may assume k is always valid, 1 ≤ k ≤ number of unique elements.
Input words contain only lowercase letters.
**Follow up:**
Try to solve it in O(n log k) time and O(n) extra space.

> 解题思路

```js
/**
 * @param {string[]} words
 * @param {number} k
 * @return {string[]}
 */
var topKFrequent = function(words, k) {
  const map = new Map();
  words.forEach((item) => map.set(item, map.get(item) ? map.get(item) + 1 : 1));
  return [...map]
    .sort((a, b) => b[1] - a[1]|| a[0].localeCompare(b[0]))
    .slice(0, k)
    .map((item) => item[0]);
};
```
