# 4 Sum II

## Takeaways
- sometimes medium q's feel like they should be easy q's
- reuse solutions for 2Sum

## Submission # 1
Not first try, but pretty quick, with help.

Time: O(N^2)
Space: O(N^2)

```javascript
function fourSumCount(nums1: number[], nums2: number[], nums3: number[], nums4: number[]): number {
    let count = 0;
    const last2arraysMap = new Map();
    
    for (let i = 0; i < nums3.length; i++) {
        for (let j = 0; j < nums4.length; j++) {
            let val = nums3[i] + nums4[j];
            if (last2arraysMap.has(val)) {
                last2arraysMap.set(val, last2arraysMap.get(val) + 1);
            } else {
                last2arraysMap.set(val, 1);
            }
        }
    }
    
    for (let i = 0; i < nums1.length; i++) {
        for (let j = 0; j < nums2.length; j++) {

            let val = 0 - (nums1[i] + nums2[j]);
            
            if (last2arraysMap.has(val)) {
                count += last2arraysMap.get(val);
            }
        }
    }
    
    return count;
};
```
