# Contains Duplicate

## Takeaways

* Runtime as measured by leetcode is not accurate. I clocked wildly different (44% -> 97%) runtimes for the same code. Instead of focusing on this number, focus on time and space complexity, for which you will need to do your own analysis. In this problem, Submission #2 has a faster runtime than Submission #1 (from a couple submission attempts), but the have the same time and space complexity, with Submission #1 having an average runtime probably faster than Submission #2 at high values of `nums.length`due to not needing to traverse the entire array before returning.

## Submission #1

Made an effort to use a hash table (`Map`) for quick lookup of duplicate values, but using an Object would have the same effect.

Memory: 45.2 MB

Language: **Typescript**

Time Complexity: **O(n)**

Space Complexity: **O(n)**

Runtime: **110 ms**

Memory: **45.2 MB**

```typescript
function containsDuplicate(nums: number[]): boolean {
    const numCountMap: Map<number, number> = new Map<number, number>();
    
    for (let i = 0; i < nums.length; i++) {
       if (numCountMap.has(nums[i])) {
           return true;
       } else {
           numCountMap.set(nums[i], 1);
       }        
    }

    return false;
};
```

## Submission #2

Looked at discussions to find this elegant `Set` solution.

Language: **Typescript**

Time Complexity: **O(n)**

Space Complexity: **O(n)**

```typescript
function containsDuplicate(nums: number[]): boolean {
    return nums.length !== (new Set(nums)).size;
};
```

