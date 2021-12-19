# Unique Paths
## Takeaways
- Remember how to build 2D arrays in js...

## Solution 1
Took > 60 mins to solve, with help from Bernadette and numerous array issues.

```js
/**
 * @param {number} m
 * @param {number} n
 * @return {number}
 */
var uniquePaths = function(m, n) {
    // m = 3, n = 2 -> 3
    // m = 2, n = 3 -> 3
    // m = 3, n = 3 -> 3
    
    const memo = [];
    for (let i = 0; i < m; i++) {
        memo.push(Array(n).fill(null));
    }
    
    return pathsMemo(m, n, memo);
    
    
};
    
function pathsMemo(m, n, memo) {
    let result;
    
    if (memo[m - 1][n - 1]) {
        return memo[m - 1][n - 1];
    }
   
    
    if (m === 1 || n === 1) {
         memo[m - 1][n - 1] = 1;
        return 1;
    }
    
    let left = pathsMemo(m - 1, n, memo)
    let right = pathsMemo(m, n - 1, memo);
    result = left + right;
    
     memo[m - 1][n - 1] = result;
    return result;
}
```