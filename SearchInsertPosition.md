# Search Insert Position
  
difficulty: Easy  
  
Given a sorted array of distinct integers and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.  
  
You must write an algorithm with O(log n) runtime complexity.
  
 

Example 1:
```
Input: nums = [1,3,5,6], target = 5
Output: 2
```
Example 2:
```
Input: nums = [1,3,5,6], target = 2
Output: 1
```
Example 3:
```
Input: nums = [1,3,5,6], target = 7
Output: 4
```

Constraints:
```
1 <= nums.length <= 104
-104 <= nums[i] <= 104
nums contains distinct values sorted in ascending order.
-104 <= target <= 104
```
Leetcode link: https://leetcode.com/problems/search-insert-position

# Solution

```
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number}
 */
var searchInsert = function(nums, target) {
    //O(logn) means binary search
    let left = 0;
    let right = nums.length - 1;
    let m = left + Math.floor((right - left)/2);
    while(true) {
        //console.log(left, m, right);
        if (nums[m] ===  target) return m;
        if (left >= right) {
            if (nums[left] < target) {
                return left + 1;
            }
            if (nums[left] > target) {
                return left;
            }
        }
        if (nums[m] > target) {
            //go left
            right = m - 1;
        }

        if (nums[m] < target) {
            //go right
            left = m + 1;
        }
        m = left + Math.floor((right - left)/2);
    }
};
```

![Search Insert Position](./img/SearchInsertPosition1.png)