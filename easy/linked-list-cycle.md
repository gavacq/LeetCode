# Linked List Cycle

## Submission #1

First try success! Nothing special here.

Time Complexity: **O(n)**

Space Complexity: **O(n)**

```typescript
/**
 * Definition for singly-linked list.
 * class ListNode {
 *     val: number
 *     next: ListNode | null
 *     constructor(val?: number, next?: ListNode | null) {
 *         this.val = (val===undefined ? 0 : val)
 *         this.next = (next===undefined ? null : next)
 *     }
 * }
 */

function hasCycle(head: ListNode | null): boolean {
    const listMap: Map<ListNode, number> = new Map();
    let i: number = 0;
    
    while (head) {
        if (listMap.has(head)) {
            return true;
        }
        
        listMap.set(head, i++);
        head = head.next;
    }
    
    return false;
};
```

Could have also used [Fast and Slow Runner aka Floyd's cycle detection algorithm](https://codeburst.io/fast-and-slow-pointer-floyds-cycle-detection-algorithm-9c7a8693f491) for **O(1)** space complexity.

```javascript
function hasCycle(head) {
    let fast = head
    let slow = head
    while (fast && fast.next) {
        fast = fast.next.next
        slow = slow.next
        if (fast == slow) return true
    }
    return false
}
```

