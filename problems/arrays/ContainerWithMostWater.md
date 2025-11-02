# Container With Most Water

You are given an integer array height of length n. There are n vertical lines drawn such that the two endpoints of the ith line are (i, 0) and (i, height[i]).  
  
Find two lines that together with the x-axis form a container, such that the container contains the most water.  
  
Return the maximum amount of water a container can store.  
  
Notice that you may not slant the container.  
  
Example 1:

![ContainerWithMostWater.jpg](./img/ContainerWithMostWater.jpg)
```
Input: height = [1,8,6,2,5,4,8,3,7]
Output: 49
Explanation: The above vertical lines are represented by array [1,8,6,2,5,4,8,3,7]. In this case, the max area of water (blue section) the container can contain is 49.
```
Example 2:
```
Input: height = [1,1]
Output: 1
```

Constraints:
```
n == height.length
2 <= n <= 105
0 <= height[i] <= 104
```

Leetcode Link: https://leetcode.com/problems/container-with-most-water

# Solution

## `O(n**2)`

```
/**
 * @param {number[]} height
 * @return {number}
 */
var maxArea = function(height) {
    // if there are only two items in the height arry, then the result is the loweritem * 1
    // use lowerItem and max to keep the recode, O(n**2)
    let lowerItem = 0;
    let max = 0;
    for (let i = 0; i < height.length; i++){
        for (let j=i+1; j < height.length; j++) {
            if (height[i] < height[j]) {
                lowerItem = height[i];
            } else {
                lowerItem = height[j];
            }

            if (max < lowerItem*(j-i)) {
                max = lowerItem*(j-i);
            }
        }
    }
    return max;
}; 
```
This algorithm is not good if there is a big height array, Time Limit Exceeded.


## O(n) by Greedy Algorithm

```
/**
 * @param {number[]} height
 * @return {number}
 */
var maxArea = function(height) {
    // start from both side, two pointer
    let left = 0; // left pointer
    let right = height.length - 1; // right pointer
    let max = 0; // the max value
    let smaller = 0; // the smaller value in left and right
    let distance;
    while (left < right) {
        distance = right - left;
        if (height[left] < height[right]) {
            smaller = height[left];
            left++;
        } else {
            smaller = height[right];
            right--;
        }
        
        if (max < smaller * distance) {
            max = smaller * distance;
        }
    }
    return max;
};
```
Solution visualizer: [Container With MostWater](./ContainerWithMostWater.html)
![ContainerWithMostWater1.png](./img/ContainerWithMostWater1.png)