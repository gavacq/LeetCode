# Product of Array Except Self

## Takeaways

* When problem involves doing something to each element of an array, consider working backwards through the array.
* To improve time complexity, consider sacrificing space complexity. E.g. storing calculations in memory

## Submission #1

Failed due to time limit exceeded. I was initialising each temporary array with `new Array(n)` which uses extra `n` time , when I should have done `[]` as there is no need to worry about out-of-bounds access since JS will dynamically allocate for us.

## Submission #2

Success! Use `n` less memory since we don't need to store the product of `pre` and `post` arrays in a new array.

Time Complexity: **O(n)**

Space Complexity: **O(n)**

```typescript
function productExceptSelf(nums: number[]): number[] {
    let prevProd: number = 1;
    let postProd: number = 1;
    const prevArr: number[] = []
    const postArr: number[] = []
    const result: number[] = []
    
    for (let i = 0; i < nums.length; i++) {
        
        if (i > 0 ) {
            prevProd *= nums[i - 1];
            postProd *= nums[nums.length - i];
            prevArr[i] = prevProd;
            postArr[nums.length - i - 1] = postProd;
        }
        if (i === 0) {
            prevArr[0] = 1;
            postArr[nums.length - 1] = 1;
        }
    }
    
    for (let i = 0; i < nums.length; i++) {
        result[i] = prevArr[i] * postArr[i];
    }
    
    
    return result;
   
};
```

