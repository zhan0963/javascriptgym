# Longest Common Prefix

## Problem

Write a function to find the longest common prefix string amongst an array of strings.  

  
If there is no common prefix, return an empty string `""`.  
  
  
  
Example 1:
```
Input: strs = ["flower","flow","flight"]
Output: "fl"
```
Example 2:
```
Input: strs = ["dog","racecar","car"]
Output: ""
Explanation: There is no common prefix among the input strings.
```

Constraints:
```
1 <= strs.length <= 200
0 <= strs[i].length <= 200
strs[i] consists of only lowercase English letters if it is non-empty.
```

Leetcode link:
https://leetcode.com/problems/longest-common-prefix

## Solution 1

```
/**
 * @param {string[]} strs
 * @return {string}
 */
var longestCommonPrefix = function(strs) {
    let prefix = strs[0]; 
    for (let i = 1; i < strs.length; i++) {
        if (prefix.length > strs[i].length) {
            prefix = strs[0].slice(0, strs[i].length);
        }
        //console.log(prefix);
        for (let j = 0; j < prefix.length; j++) {
            if (prefix[j] !== strs[i][j]) {
                if (j == 0) return "";
                prefix = prefix.slice(0, j);
                break;
            } 
        }
    }
    return prefix;
};
```

![LongestCommonPrefix1.png](./img/LongestCommonPrefix1.png)

## Solution 2

By using string.indexOf(prefix), reduce the time complexity

```
/**
 * @param {string[]} strs
 * @return {string}
 */
var longestCommonPrefix = function(strs) {
    let prefix = strs[0]; 
    for (let i = 1; i < strs.length; i++) {
        if (prefix.length > strs[i].length) {
            prefix = strs[0].slice(0, strs[i].length);
        }
        
        while(strs[i].indexOf(prefix) !== 0) {
            prefix = prefix.slice(0, -1);
            if (!prefix) return "";
        }
    }
    return prefix;
};
```

![LongestCommonPrefix2.png](./img/LongestCommonPrefix2.png)