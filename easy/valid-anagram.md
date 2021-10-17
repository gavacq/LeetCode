# Valid Anagram

## Takeaways

## Submission #1

First try success! Was not a complicated problem, but I wanted to have an efficient solution, so I used a hash table. I incremented the value associated with a letter if it was present in the first string, and decremented if it was in the second string.

**Challenge:** How to alter solution for unicode characters?

* I would use `string.charCodeAt()` to get the UTF-16 representation of each character in a string and use that as the key into the hash table

Language: **Typescript**

Time Complexity: **O(n)**

Space Complexity: **O(n)**

```typescript
function isAnagram(s: string, t: string): boolean {
    // store letter counts of s and t in two hash tables and compare for equality?
    const charMap: Map<string, number> = new Map<string, number>();
    if (s.length !== t.length) {
        return false;
    }
    
    // build hash tables
    let sTemp: number = 0;
    let tTemp: number = 0;
    for (let i = 0; i < s.length; i++) {
        sTemp = charMap.get(s[i]) ? charMap.get(s[i]) + 1 : 1
        charMap.set(s[i], sTemp);
        tTemp = charMap.get(t[i]) ? charMap.get(t[i]) - 1 : -1
        charMap.set(t[i], tTemp);
    }
    
    const charMapValues = charMap.values()
    for (const n of charMapValues) {
        if (n !== 0) {
            return false;
        }
    }
    
    return true;
};
```

## **Alternate Solutions**

* can sort the strings first then compare them. This is slower at **O(nlogn)**

