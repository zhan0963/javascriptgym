# Longest Substring Without Repeating Characters

Given a string s, find the length of the longest substring without duplicate characters.  
  
   
  
Example 1:
```
Input: s = "abcabcbb"
Output: 3
Explanation: The answer is "abc", with the length of 3. Note that "bca" and "cab" are also correct answers.
```
Example 2:
```
Input: s = "bbbbb"
Output: 1
Explanation: The answer is "b", with the length of 1.
```
Example 3:
```
Input: s = "pwwkew"
Output: 3
Explanation: The answer is "wke", with the length of 3.
Notice that the answer must be a substring, "pwke" is a subsequence and not a substring.
```

Constraints:
```
0 <= s.length <= 5 * 104
s consists of English letters, digits, symbols and spaces.
```

Leetcode Link: https://leetcode.com/problems/longest-substring-without-repeating-characters

# Solutions

```
/**
 * @param {string} s
 * @return {number}
 */
var lengthOfLongestSubstring = function(s) {
    let strObj = {};
    let start = 0;
    let end = 0;
    let max = 0;

    for (;end < s.length; end++) { 
        if (strObj[s[end]] !== undefined) {
            if (max < (end - start)) {
                max = (end - start); // keep the max record
            }

            if (strObj[s[end]] >= start) { // only move start forward
                start = strObj[s[end]] + 1; // start point to the first repeat item position + 1
            }
        } 
        strObj[s[end]] = end;
    }

    return (end - start) > max? (end - start): max;
};
```

![LongestSubstringWithoutRepeatingCharacters.png](./img/LongestSubstringWithoutRepeatingCharacters.png)