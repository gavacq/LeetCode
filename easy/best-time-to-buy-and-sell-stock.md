# Best Time to Buy and Sell Stock

## Takeaways

* Unless you know that a recursive solution is correct, and will scale, it is better to come up with an iterative solution.
* To think of an iterative solution, imagine what values would need to be tracked.

## Submission #1

Failed to due heap overflow. This is due to JavaScript allocating arrays (objects) on the heap, and my code allocates arrays of size **n** recursively. The last executed input was a very long array. The long array testcase I used was not long enough to overflow...

> FATAL ERROR: Committing semi space failed. Allocation failed - JavaScript heap out of memory

```typescript
'use strict'
function maxProfit(prices: number[]): number {
    // could use nested loops to try every combination of selling
    // could also try the recursive divide and conquer strategy
    
    if (prices.length === 1) {
        // there can be no profit with only one day
        return 0
    };
    
    let maxIndex: number = getMaxIndex(prices);
    console.log('maxIndex', maxIndex)
    let minIndex: number = getMinIndex(prices);
    console.log('minIndex', minIndex)
    if (minIndex < maxIndex) {
        return prices[maxIndex] - prices[minIndex];
    } else if (minIndex > maxIndex) {
        let pricesLeft: number[] = prices.slice(0, maxIndex + 1);
        let pricesRight: number[] = prices.slice(maxIndex + 1, prices.length);
        let maxProfitLeftAndRight: number[] = [maxProfit(pricesLeft), maxProfit(pricesRight)];
        return maxProfitLeftAndRight[getMaxIndex(maxProfitLeftAndRight)];
    } else {
        return 0;
    }
    
    
}

function getMaxIndex(prices: number[]): number {
    let max: number = 0;
    let maxIndex: number = 0;
    
    prices.forEach((n, i) => {
        if (n > max) {
            maxIndex = i;
            max = n;
        }
    })
    
    return maxIndex;
}

function getMinIndex(prices: number[]): number {
    let min = Infinity
    let minIndex: number = 0;
    
    prices.forEach((n, i) => {
        if (n < min) {
            minIndex = i;
            min = n;
        }
    })
    
    return minIndex;
}
```

## Submission #2

Looked at discussions since I couldn't figure out how to improve... and boy do I feel dumb. The best solution iterates through the array one time, keeping track of the maximum profit, as well as the minimum value. This works because we are checking the  difference of the current value against the previous minimum value, guaranteeing that we will catch a possible max profit from selling the minimum value in the future. If the max profit ended up being the different of two values before this minimum value, then we would have saved the profit already, and would never overwrite.

Time Complexity: **O(n)**

Space Complexity: **O(1)**

```typescript
function maxProfit(prices: number[]): number {
    let min: number = Infinity;
    let max = 0;
    
    for (let i = 0; i < prices.length; i++) {
        min = Math.min(min, prices[i]);
        max = Math.max(max, prices[i] - min);
    }
    
    return max;
}
```



