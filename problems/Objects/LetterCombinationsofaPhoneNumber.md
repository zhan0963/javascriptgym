# Letter Combinations of a Phone Number

Given a string containing digits from 2-9 inclusive, return all possible letter combinations that the number could represent. Return the answer in any order.  
  
A mapping of digits to letters (just like on the telephone buttons) is given below. Note that 1 does not map to any letters.  

<img src="./img/LetterCombinationsofaPhoneNumber.png" width=100 height=100 />
<!-- ![LetterCombinationsofaPhoneNumber.png](./img/LetterCombinationsofaPhoneNumber.png) -->

Example 1:
```
Input: digits = "23"
Output: ["ad","ae","af","bd","be","bf","cd","ce","cf"]
```
Example 2:
```
Input: digits = "2"
Output: ["a","b","c"]
```

Constraints:
```
1 <= digits.length <= 4
digits[i] is a digit in the range ['2', '9'].
```

Leetcode link: https://leetcode.com/problems/letter-combinations-of-a-phone-number

# Solution

```
/**
 * @param {string} digits
 * @return {string[]}
 */
var letterCombinations = function(digits) {
    const dmap = {
        2: ['a','b','c'],
        3: ['d','e','f'],
        4: ['g','h','i'],
        5: ['j','k','l'],
        6: ['m','n','o'],
        7: ['p','q','r','s'],
        8: ['t','u','v'],
        9: ['w','x','y','z']
    }

    const output = [];
    function backtrack(index, current) {
        if (index === digits.length) {
            output.push(current);
            return;
        }

        const letters = dmap[digits[index]];

        for (const letter of letters) {
            backtrack(index+1, current + letter);
        }
    }

    backtrack(0, '');
    return output;
    
};
```

![LetterCombinationsofaPhoneNumber1.png](./img/LetterCombinationsofaPhoneNumber1.png)