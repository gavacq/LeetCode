# 3Sum

## Takeaways
- Starting a loop at the index after a previous loop is a efficiency trick to prevent using the same element twice
- if you have an algorithm with a larger time complexity (e.g. O(N * N^2) = O(N^3) for 3Sum brute force), it can be a good idea to see if sorting can reduce the time (e.g. O(Nlog(N) + N^2) = O(N^2)).

## Submission # 1

I couldn't find a solution in 30 mins, and couldn't even remember a solution to 2Sum... I need to practice LeetCode more and review my past solutions. Maybe I should make some specific practice plan...?

```typescript
function threeSum(nums: number[]): number[][] {
    let num1 = nums[0]; 
    const result = [];
    
    if (nums.length < 2) {
        return [];
    }
    
    for (let i = 0; i < nums.length; i++) {
        
        const twoSumRes = twoSum(-i, nums);
        if (twoSumRes.length) {
            result.push([i, twoSumRes[0], twoSumRes[1]])
        }
    }
    
    

    
    return result;
};

function twoSum(target: number, nums: number[]): number[][] {
    
    const map = new Map();
    for (let i = 0; i < nums.length; i++) {
        if (i === -1 * target) continue;
        for (let j = 0; j < nums.length; j++) {
            
            if (j === -1 * target) continue;
            Map.set(nums[i] + nums[j], 1);
        }
    }
    
    for (let i = 0; i < nums.length; i++) {
        if (Map.get(target)) {
            return([i, -1 * nums[i]])
        }
    }
    
}




    for (let i = 0; i < nums.length; i++) {
        
        num1 = nums[i];
        for (let j = 0; j < nums.length; j++) {
            if (num1 + nums[i + 1] === 0) {
               result.push([num1, nums[j]]);
               break;
            }
        }
    }
```

## Submission # 2
Looked at the solution https://www.youtube.com/watch?v=jXZDUdHRbhY

Time: O(N^2)
Space: O(N)


```javascript
function threeSum(nums: number[]): number[][] {
    nums.sort((a,b) => a - b)
    const results = [];
    const seen = new Map();
    
    if (nums.length < 3) return [];
    
    for (let i = 0; i < nums.length - 2; i++) {
        let partial_target = undefined;
        let partial_sum_nums = undefined;
        if (seen.has(nums[i])) continue;
        else {
            partial_target = 0 - nums[i];
            seen.set(nums[i], true);
        }
        
        let j = i + 1;
        let k = nums.length - 1;
        
        while (j < k) {
            let partial_sum = nums[j] + nums[k];
            if (partial_sum === partial_target) {
                partial_sum_nums = seen.get(nums[i])
                if (!(partial_sum_nums[0] === nums[j] && partial_sum_nums[1] === nums[k])) {
                    results.push([nums[i], nums[j], nums[k]]);
                    seen.set(nums[i], [nums[j], nums[k]])
                }
            }
            
            if (partial_sum > partial_target) {
                // make sum smaller
                k -= 1;
            } else {
                j += 1;
            }
        }
    }
        
    return results;
    
}
```