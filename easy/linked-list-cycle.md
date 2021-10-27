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

