# Valid Palindrome

A phrase is a palindrome if, after converting all uppercase letters into lowercase letters and removing all non-alphanumeric characters, it reads the same forward and backward. Alphanumeric characters include letters and numbers.  
  
Given a string s, return true if it is a palindrome, or false otherwise.  
  
 

Example 1:
```
Input: s = "A man, a plan, a canal: Panama"
Output: true
Explanation: "amanaplanacanalpanama" is a palindrome.
```
Example 2:
```
Input: s = "race a car"
Output: false
Explanation: "raceacar" is not a palindrome.
```
Example 3:
```
Input: s = " "
Output: true
Explanation: s is an empty string "" after removing non-alphanumeric characters.
Since an empty string reads the same forward and backward, it is a palindrome.
```
 

Constraints:
```
1 <= s.length <= 2 * 105
s consists only of printable ASCII characters.
```

Leetcode Link: https://leetcode.com/problems/valid-palindrome

# Solution

```
/**
 * @param {string} s
 * @return {boolean}
 */
var isPalindrome = function(s) {
    // start from both side
    let left = 0;
    let right = s.length - 1;
    while(left<=right) {
        //console.log(s[left], s[right])
        if (!isAlphanumeric(s[left])) {
            left++;
            continue;
        }

        if (!isAlphanumeric(s[right])) {
            right--;
            continue;
        }

        if (s[left].toLowerCase() !== s[right].toLowerCase()) return false;
        left++;
        right--;
    }

    return true;


    function isAlphanumeric(char) {
	    // Checks if the character matches any letter (case-insensitive) or any digit.
	    return /^[a-zA-Z0-9]$/.test(char);
	}
    
};
```

![ValidPalindrome1.png](./img/ValidPalindrome1.png)