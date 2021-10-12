# Largest Odd Number in String

## Takeaways

* always add additional test cases since the provided cases are not exhaustive

## Submission #1

Failure at testcase `"239537672423884969653287101"` due to overflowing `Number()` cast.  Need to use 

```typescript
function largestOddNumber(num: string): string {
    let max: number = -Infinity;
    
    for (let j = 0; j < num.length; j++) {
        for (let i = j + 1; i <= num.length; i++) {
            let subNum: number = Number(num.slice(j,i));
        
            if (subNum > max && subNum % 2 !== 0) {
                max = subNum;
            }
        }    
    }
    
    return max !== -Infinity ? max.toString() : "";
};
```

## Submission #2

Failure due to timeout. 1000 character string at O(n^2) runtime is too slow. Need to not loop through every substring...

```typescript
function largestOddNumber(num: string): string {
    let max: string = "";
    
    for (let j = 0; j < num.length; j++) {
        for (let i = j + 1; i <= num.length; i++) {
            // get substring
            let subNum: string = num.slice(j,i);
            //check substr last digit is odd number and length > max.length
            
            if (Number(subNum[subNum.length - 1]) % 2 !== 0 && isLarger(subNum, max) ) {
                max = subNum;
            }
        }    
    }
    
    return max;
};

function isLarger(num: string, max: string): boolean {
    if (max.length > num.length) {
        return false;
    }

    for (let i = 0; i < num.length; i++) {
        if (i > max.length - 1 || num[i] > max[i]) {
            return true;
        }
    }
    
    return false;
}
```

## Submission #3

Had to look at Discussions to get faster solution. The key is to start looking from the end of the string, since if any odd number is found, the substring starting at index 0 to that odd number will be the largest odd substring in the input string. I was trying to keep track of the max, when I could instantly find the max by looking from the end.

```typescript
function largestOddNumber(num: string): string {
    for (let i = num.length - 1; i >= 0; i--) {
        if (Number(num[i]) % 2 !== 0) return num.substring(0, i + 1)
    }
    
    return ""
};
```

