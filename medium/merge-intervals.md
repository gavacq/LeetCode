# Merge Intervals

## Takeaways

* if problem looks simpler to solve after sorting (asc, desc, etc.), try to do so. Recall how to use `Array.sort()`
* if you need to compare two values to decide what to update, remember to use `Math.max()`
* remember that arrays are stored by reference, so you can get a reference to an array and update it, while continuing to iterate through another array

## Submission # 1

Could not find a solution that worked for all cases.. my logic was too complicated and conditional.

```typescript
function merge(intervals: number[][]): number[][] {
    const result: number[][] = [];
    result[0] = [intervals[0][0],intervals[0][1]];
    for (let i = 1; i < intervals.length; i++) {
        if (!checkIntervals(intervals, i, result)) {
            result[result.length] = [intervals[i][0], intervals[i][1]];
        }
    }
        
    return result;
};

function checkIntervals(intervals: number[][], i: number, result: number[][]) : boolean {
    for (let j = 0; j < result.length; j++) {
        console.log('results total', result)
        console.log('intervals total', intervals)
        console.log(intervals[i])
        if (intervals[i][0] <= result[j][0]) {
            if (intervals[i][1] >= result[j][1]) {
                result[j][1] = intervals[i][1];
                result[j][0] = intervals[i][0];
                return true;
            }
            if (intervals[i][1] >= result[j][0]) {
                result[j][0] = intervals[i][0];
                return true;
            } else {
                if (result.length === 1) {
                    result.unshift([intervals[i][0], intervals[i][1]]);
                } else {
                    result.splice(j - 1, 0, [intervals[i][0], intervals[i][1]])
                }
                return true;
            }

        }

        if (intervals[i][0] <= result[j][1]) {
            if (intervals[i][1] >= result[j][1]) {
                result[j][1] = intervals[i][1];
                console.log('break second');
                console.log('j', j)
                console.log('res',result[j])
                return true;
            } else {
                console.log('break third');
                console.log('res',result[j])
                return true;
            }
        }
    }
    
    return false;
}
```

## Submission #2

Read discussions. Requires `Array.sort`first, then `Math.max`.

Time Complexity: **O(nlogn)**

Space Complexity: **O(1)**

```typescript
function merge(intervals) {
  if (!intervals.length) return intervals
  intervals.sort((a, b) => a[0] - b[0])
  var prev = intervals[0]
  var res = [prev]
  for (var curr of intervals) {
    if (curr[0] <= prev[1]) {
      prev[1] = Math.max(prev[1], curr[1])
    } else {
      res.push(curr)
      prev = curr
    }
  }
  return res
}
```

