# Longest Palindromic Substring

Given a string s, return the longest palindromic substring in s.  
  
 

Example 1:
```
Input: s = "babad"
Output: "bab"
Explanation: "aba" is also a valid answer.
```
Example 2:
```
Input: s = "cbbd"
Output: "bb"
```

Constraints:
```
1 <= s.length <= 1000
s consist of only digits and English letters.
```

Leetcode Link: https://leetcode.com/problems/longest-palindromic-substring

# Solution

```
/**
 * @param {string} s
 * @return {string}
 */
var longestPalindrome = function(s) {
    const LEFT = 0;
    const RIGHT = s.length - 1;
    const max = {
        len: 0,  // the max length
        substr: '', // the longest palindromic substring
    }

    if (s.length > 0) { // 1 char is the smallest palindromic substring
        max.len = 1;
        max.substr = s[0];
    }

    for (let i = 0; i < RIGHT; i++) {
        // we don't care if the first item and the last
        // for each i, we need to check 2 situation
        // 1. 'aba', i is the center
        // 2. 'bb' i and i+1 is the center
        let j = 1;
        let l = 0;
        while ((i-j) >= LEFT && (i+j) <= RIGHT && (s[i-j] === s[i+j])) {
            l = 2*j+1;
            if (l > max.len) {
                max.len = l;
                max.substr = s.slice(i-j, i+j+1);
            }
            //console.log(i,'j:',j,l,s.slice(i-j, i+j+1),max);
            j++;
        }

        let k = 1;
        while ((i+1-k) >= LEFT && (i+k) <= RIGHT && s[i+1-k] === s[i+k]) {
            l = 2*k;
            if (max.len < l) {
                max.len = l;
                max.substr = s.slice(i+1-k, i+k+1);
            }
            //console.log(i,'k:',k,l,s.slice(i+1-k, i+k+1),max);
            k++;
        }       
    }
    return max.substr;
    
};


```

![LongestPalindromicSubstring1.png](./img/LongestPalindromicSubstring1.png)