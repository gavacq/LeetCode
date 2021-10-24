# Maximum Subarray

## Takeaways

* Try to use built-in JS methods like `Math.max` to reduce conditional (`if...else`) clutter.

## Submission 1

First try success. Kept track of `sum` (used like `prev`) to update the starting position of the sub-array. 

Time Complexity: **O(n)**

Space Complexity: **O(1)**

```typescript
function maxSubArray(nums: number[]): number {
    let max: number = -Infinity;
    let sum: number = 0;
    
    nums.forEach((e) => {
        sum += e;
        if (e > sum) {
            sum = e;
        }
        
        if (sum > max) {
            max = sum;
        }
    })
    
    return max;
};
```

