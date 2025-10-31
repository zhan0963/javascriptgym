# Pascal's Triangle

Given an integer numRows, return the first numRows of Pascal's triangle.  
  
In Pascal's triangle, each number is the sum of the two numbers directly above it as shown:  

![PascalTriangleAnimated2.gif](./img/PascalTriangleAnimated2.gif)

Example 1:
```
Input: numRows = 5
Output: [[1],[1,1],[1,2,1],[1,3,3,1],[1,4,6,4,1]]
```
Example 2:
```
Input: numRows = 1
Output: [[1]]
```

Constraints:
```
1 <= numRows <= 30
```

Leetcode link: https://leetcode.com/problems/pascals-triangle

# Solution

```
/**
 * @param {number} numRows
 * @return {number[][]}
 */
var generate = function(numRows) {
    const resultArr = [];
    for (let i = 0; i < numRows; i++) {
        resultArr[i] = row(i+1, resultArr[i-1]);
    }
    return resultArr;

    function row(rownum, upperArr=[]){
        //return a numArr from number
        // the numth row has num item
        if (rownum === 1) return [1];
        const numArr = [];
        for (let i = 0; i < rownum; i++){
            upleft = ((i-1) < 0)?0:upperArr[i-1];
            upright = (i === (rownum - 1))?0:upperArr[i];
            //console.log(rownum,i,upleft, upright);
            numArr[i] = upleft + upright;
        }
        return numArr;
    }
};
```

![PascalsTriangle.png](./img/PascalsTriangle.png)