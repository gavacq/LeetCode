# Valid Parentheses

## Takeaways

## Submission #1

Second try success, had to check that all brackets had been closed (`brackets.length === 0`) . Algorithm was not too difficult and I'm happy with the solution I came up with: add only closing brackets to a `brackets` array.

Language: **Typescript**

Time Complexity: **O(n)**

Space Complexity: **O(n)**

```typescript
function isValid(s: string): boolean {
    const brackets: string[] = [];
    
    for (let i = 0; i < s.length; i++) {
        if (isOpenBracket(s[i])) {
            brackets.push(closingBracket(s[i]));
        } else if (brackets.length && brackets[brackets.length - 1] === s[i]) {
            brackets.pop();
        } else {
            return false;
        }
    }
    
    return brackets.length ? false: true;
};

function isOpenBracket(c: string): boolean {
    return (c === '(' || c === '{' || c === '[');
}

function closingBracket(c: string): string {
    switch (c) {
        case '(':
            return ')';
        case '[':
            return ']';
        case '{':
            return '}';
        default: return ')'
    }
}
```

