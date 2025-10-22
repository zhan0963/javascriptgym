# Find the Index of the First Occurrence in a String

Given two strings needle and haystack, return the index of the first occurrence of needle in haystack, or -1 if needle is not part of haystack.  
  
 

Example 1:
```
Input: haystack = "sadbutsad", needle = "sad"
Output: 0
Explanation: "sad" occurs at index 0 and 6.
The first occurrence is at index 0, so we return 0.
```
Example 2:
```
Input: haystack = "leetcode", needle = "leeto"
Output: -1
Explanation: "leeto" did not occur in "leetcode", so we return -1.
```

Constraints:
```
1 <= haystack.length, needle.length <= 104
haystack and needle consist of only lowercase English characters.
```

Leetcode Link: https://leetcode.com/problems/find-the-index-of-the-first-occurrence-in-a-string

# Solution

For Javascript, there is a string prototype method "indexOf" can deliver the same result, the algrithm behind it is applied by c++, otherwise, we can try to do it by others way. 

```
/**
 * @param {string} haystack
 * @param {string} needle
 * @return {number}
 */
var strStr = function(haystack, needle) {
    return haystack.indexOf(needle);
};
```

![FindtheIndexoftheFirstOccurrenceinaString1.png](./img/FindtheIndexoftheFirstOccurrenceinaString1.png)

# Solution 2

```
/**
 * @param {string} haystack
 * @param {string} needle
 * @return {number}
 */
var strStr = function(haystack, needle) {
    for (let i = 0; i <= (haystack.length - needle.length); i++) {
        if (haystack.slice(i, i + needle.length) === needle) return i;
    }
    return -1;
};
```

![FindtheIndexoftheFirstOccurrenceinaString2.png](./img/FindtheIndexoftheFirstOccurrenceinaString2.png)