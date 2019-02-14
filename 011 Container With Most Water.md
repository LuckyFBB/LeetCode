> 原文链接

[https://leetcode.com/problems/container-with-most-water/](https://leetcode.com/problems/container-with-most-water/)
> 题目内容

Given n non-negative integers a1, a2, ..., an , where each represents a point at coordinate (i, ai). n vertical lines are drawn such that the two endpoints of line i is at (i, ai) and (i, 0). Find two lines, which together with x-axis forms a container, such that the container contains the most water.

**Note**: You may not slant the container and n is at least 2.

![输入图片说明](https://images.gitee.com/uploads/images/2019/0111/233043_49495c94_2094786.png "屏幕截图.png")

The above vertical lines are represented by array [1,8,6,2,5,4,8,3,7]. In this case, the max area of water (blue section) the container can contain is 49.

> 解题思路

```js
/**
 * @param {number[]} height
 * @return {number}
 */
var maxArea = function (height) {
  return maxAreaRecursive(height, 0, height.length - 1);
};

var maxAreaRecursive = function (walls, left, right) {
  const height = Math.min(walls[left], walls[right]);
  const area = height * (right - left);
  if (left >= right) {
    return area;
  }
  const nextArea = walls[left] > walls[right] ? maxAreaRecursive(walls, left, right - 1) : maxAreaRecursive(walls, left + 1, right);
  return Math.max(area, nextArea);
};
```