# LEETCODE-TREES-2196
Your implementation seems to be on the right track for creating a binary tree from descriptions. Let's break down the dry run with an example input and see how it constructs the tree:

### Example Input
```
int[][] descriptions = {
  {1, 2, 1},  // Node 1 has a left child 2
  {1, 3, 0},  // Node 1 has a right child 3
  {2, 4, 1},  // Node 2 has a left child 4
  {3, 5, 0}   // Node 3 has a right child 5
};
```

### Dry Run

1. **Initialize Maps:**
   - `childToParent = {}`
   - `valToNode = {}`

2. **First Description [1, 2, 1]:**
   - `p = 1`, `c = 2`, `isLeft = 1`
   - `parent = new TreeNode(1)` (since 1 is not in `valToNode`)
   - `child = new TreeNode(2)` (since 2 is not in `valToNode`)
   - Update `valToNode`:
     - `valToNode = {1: TreeNode(1), 2: TreeNode(2)}`
   - Update `childToParent`:
     - `childToParent = {TreeNode(2): TreeNode(1)}`
   - Set `parent.left` to `child`:
     - `TreeNode(1).left = TreeNode(2)`

3. **Second Description [1, 3, 0]:**
   - `p = 1`, `c = 3`, `isLeft = 0`
   - `parent = TreeNode(1)` (already in `valToNode`)
   - `child = new TreeNode(3)` (since 3 is not in `valToNode`)
   - Update `valToNode`:
     - `valToNode = {1: TreeNode(1), 2: TreeNode(2), 3: TreeNode(3)}`
   - Update `childToParent`:
     - `childToParent = {TreeNode(2): TreeNode(1), TreeNode(3): TreeNode(1)}`
   - Set `parent.right` to `child`:
     - `TreeNode(1).right = TreeNode(3)`

4. **Third Description [2, 4, 1]:**
   - `p = 2`, `c = 4`, `isLeft = 1`
   - `parent = TreeNode(2)` (already in `valToNode`)
   - `child = new TreeNode(4)` (since 4 is not in `valToNode`)
   - Update `valToNode`:
     - `valToNode = {1: TreeNode(1), 2: TreeNode(2), 3: TreeNode(3), 4: TreeNode(4)}`
   - Update `childToParent`:
     - `childToParent = {TreeNode(2): TreeNode(1), TreeNode(3): TreeNode(1), TreeNode(4): TreeNode(2)}`
   - Set `parent.left` to `child`:
     - `TreeNode(2).left = TreeNode(4)`

5. **Fourth Description [3, 5, 0]:**
   - `p = 3`, `c = 5`, `isLeft = 0`
   - `parent = TreeNode(3)` (already in `valToNode`)
   - `child = new TreeNode(5)` (since 5 is not in `valToNode`)
   - Update `valToNode`:
     - `valToNode = {1: TreeNode(1), 2: TreeNode(2), 3: TreeNode(3), 4: TreeNode(4), 5: TreeNode(5)}`
   - Update `childToParent`:
     - `childToParent = {TreeNode(2): TreeNode(1), TreeNode(3): TreeNode(1), TreeNode(4): TreeNode(2), TreeNode(5): TreeNode(3)}`
   - Set `parent.right` to `child`:
     - `TreeNode(3).right = TreeNode(5)`

6. **Find Root:**
   - Start with `root = TreeNode(2)` (a random key from `childToParent`)
   - Traverse upwards:
     - `root = TreeNode(1)` (parent of TreeNode(2))
     - `root` is now TreeNode(1) and it has no parent in `childToParent`
   - `root` is `TreeNode(1)`

### Final Tree Structure
```
     1
    / \
   2   3
  /     \
 4       5
```

The code correctly constructs the binary tree from the descriptions and finds the root node.
