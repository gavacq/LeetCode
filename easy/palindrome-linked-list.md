# Palindrome Linked List

## Takeaways

* Slow-Fast Pointer can be used to find the middle of a linked list
* A linked list can be reversed in place using an extra pointer
* Remember the tools: **Reversing a Linked List, Slow-Fast Pointer**

## Submission #1

Took 60 mins and huge hint (reverse in place) from Bernadette, but got the solution on first submission attempt after some revisions after failing some test cases I added.

Time Complexity: **O(n)**

Space Complexity: **O(1)**

```typescript
function isPalindrome(head: ListNode | null): boolean {    
    if (!head.next) {
        return true;
    }
    
    let slow: ListNode = head.next
    let fast: ListNode = head.next.next
    let temp: ListNode = head;
    temp.next = null;
    
    while (fast && fast.next) {
        head = slow;
        slow = slow.next;
        fast = fast.next.next;
        head.next = temp;
        temp = head; 
    }
    
    // move slow pointer ahead one if odd length list
    if (fast && !fast.next) {
        slow = slow.next;
    }
    
    // head is start of reversed linked list of first half of original
    while (head && slow) {
        if (head.val !== slow.val) {
            return false
        }
        head = head.next;
        slow = slow.next;
    }
    
    return true;
};
```





