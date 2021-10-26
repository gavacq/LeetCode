# Reverse Linked List

## Takeaways

* Remember to either create new instances of a class or deep copy to avoid clobbering original pointers

## Submission #1

First try success!

Time Complexity: **O(n)**

Space Complexity: **O(n)**

````typescript
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

function reverseList(head: ListNode | null): ListNode | null {
    let reversedList: ListNode | null = null;
    if (head) {
       reversedList = new ListNode(head.val, null);
    } else {
        return null;
    }
    
    while (head.next) {
       let tempNode: ListNode = reversedList;
       reversedList = new ListNode(head.next.val, tempNode);
       head = head.next;
    }

    return reversedList;
};
````

