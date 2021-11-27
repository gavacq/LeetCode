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