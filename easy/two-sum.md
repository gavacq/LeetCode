# Two Sum
#easy #twosum 

## Submission #1

Complexity: **O(n^2)**

Runtime: **104 ms**

Memory Usage: **39.5 MB**

Description: Nested for loops

```js
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
var twoSum = function(nums, target) {
    for (let i = 0; i < nums.length; i++) {
        for (let j = i + 1; j < nums.length; j++) {
            if (nums[i] + nums[j] === target) {
                return [i,j]
            }
        }
    }  
};
```

## Submission #2

Complexity: **O(n)**

Runtime: **72 ms**

Memory Usage: **42.1 MB**

Description: Hash map

```js
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
var twoSum = function(nums, target) {
    let ans=[];
    let map = new Map();

    for(let i=0;i<nums.length;i++) {
        map.set(nums[i],i);
    }
    
    for(let i=0;i<nums.length;i++) {
        if(map.has(target-nums[i]) && map.get(target-nums[i])!=i){
            ans.push(i)
            ans.push(map.get(target-nums[i]));
            break;
        }
    }
    
    return ans;
}
```

