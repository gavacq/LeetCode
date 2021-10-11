# Binary Tree Inorder Traversal

## Takeaways

- it is important to remember to build helper functions for algorithms

- Binary tree depth first algorithms are applied recursively to each sub-tree, where a sub-tree just has three nodes, any of which could be null.

  root

​	/        \

left		right

```typescript
/**
 * Definition for a binary tree node.
 * class TreeNode {
 *     val: number
 *     left: TreeNode | null
 *     right: TreeNode | nullTakeaways: **It is important to remember to build helper functions for algorithms!**
 *     constructor(val?: number, left?: TreeNode | null, right?: TreeNode | null) {
 *         this.val = (val===undefined ? 0 : val)
 *         this.left = (left===undefined ? null : left)
 *         this.right = (right===undefined ? null : right)
 *     }
 * }
 */
```

## Submission #1

- Language: **Typescript**
- Complexity: **TODO** 
- Runtime: **106 ms, faster than 24.29%**
- Memory: **40.7 MB, less than 27.79% **

```typescript
function inorderTraversal(root: TreeNode | null): number[] {
    const output = [];
    if (root && root.left) {
        output.push(...inorderTraversal(root.left));        
    };
    
    if (root) {
        output.push(root.val);        
    };

    if (root && root.right) {
        output.push(...inorderTraversal(root.right));    
    };
    
    return output;
};
```

This solution is pretty slow and uses the spread operator to lazily add values in arrays returned from recursive calls to the parent array. I should come up with a more efficient solution.

### Submission #2

Looked at discussions. This solution uses a helper function `inorder` that takes the `result` array as an argument so that `result` can be updated one element at a time, instead of using the spread operator.

- Language: **Typescript**
- Complexity: **TODO** 
- Runtime: **102 ms, faster than 26.48%**
- Memory: **40.3 MB, less than 74.62%**

```typescript
function inorderTraversal(root: TreeNode | null): number[] {
    const result: number[] = [];
    
    inorder(root, result);
    
    return result;
};

function inorder(root: TreeNode | null, result: number[]) {
    if (!root) return;
    
    inorder(root.left, result);
    result.push(root.val);
    inorder(root.right, result);
}
```