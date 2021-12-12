# Climbing Stairs

## Takeaways

## Submission #1
- lots of hints from Bernadette and went overtime by 10 minutes but got a top-down solution with memoization. Unfortunately this is still too slow..

time: ?
space: O(N)

```js
function climbStairs(n: number): number {
// 1 * takesOne = ones
// 2 * takesTwo = twos`
// n = ones + twos

    // n = 3
    // iterate from 1 to n, adding 2 each time
    // at n, we have one combination
    // more than n, we have use a takesOne
    
    // n = 2 , n = 1
    // n = 1, one possibility, takesOne = 1
    // n = 2, two possibilities, takesOne = 2, takesTwo = 1
    
    // climbStairs(n - 1)
    // climbStairs(3 - 1) -> climbStairs(2)
    // if n 
    // climbStairs(2) -> climbStairs(1)
    
    // n = 5, start = 2
    // -> 3
    // climb(n - start)
    // -> climb(n - 1)
    
    // let combos = 0;
    // combos += climb(n - 2)
    // combos += climb(n - 1)
    
    // climb
    // 1 + 1 + 1
    // 1 + 2
    // 2 + 1
    
    // climbStairs(4 - 1) = 3 + 
    // 1 + 1 + 1 + 1
    // 1 + 2 + 1
    // 1 + 1 + 2
    // 2 + 1 + 1
    // 2 + 2
    
    // climbStair(5 - 1)
    // 1 + 1 + 2 + 1
    // 1 + 2 + 2
    // 2 + 2 + 1
    // 2 + 1 + 2
    // 2 + 1 + 1 + 1
    
    // base case : 1 stair
    // 
    
    const memo = Array(n).fill(undefined);
    return climbMemo(n, memo)
    
};

function climbMemo(n, memo) {
    
    if (n === 1) {
        return 1;
    }
    
    if (n === 2) {
        return 2;
    }
    
    if (memo[n]) return memo[n];
    
    let combos = 0;
    combos += climbStairs(n - 1); // climb(3)
    combos += climbStairs(n - 2); // climb(2)
    memo[n] = combos;
    return combos;
}
```

## Submission #2
- bottom up solution, note the resemblance to fibonacci

```typescript
function climbStairs(n: number): number {
    if (n === 1) {
        return 1;
    }
    
    if (n === 2) {
        return 2;
    }
    
    const memo: number[] = Array(n).fill(undefined);
    memo[0] = 1;
    memo[1] = 2;
    
    for (let i: number = 2; i < n; i++) {
        memo[i] = memo[i - 1] + memo[i - 2];
    }    
    
    return memo[n - 1];    
};
```