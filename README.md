# Leetcode_Untouched – Problem 404: Sum of Left Leaves 🌱

This repository provides a **unique, efficient, and optimized solution** to [LeetCode Problem 404 – Sum of Left Leaves](https://leetcode.com/problems/sum-of-left-leaves/).  
The goal is to clearly explain the thought process, approach, and implementation.

---

## 📖 Intuition
To solve this problem, we need to identify all the **left leaf nodes** in the binary tree.  
A *left leaf* is a leaf node that is the **left child of its parent**.  

We can traverse the tree using a **Depth-First Search (DFS)** approach:
- Recursively check each node.  
- If a node is a left child *and* is a leaf (both its left and right children are null), we add its value to the sum.  
- By using DFS, we efficiently explore each node while only considering left leaves.

---

## 🛠️ Approach
We perform a depth-first traversal of the binary tree:  
1. **Base Case** → If the node is `null`, return `0`.  
2. **Leaf Check** → If the node is a leaf (no children) and is a left child, return its value.  
3. **Recursive Case** → If not a leaf, recursively explore both subtrees:  
   - For the **left child**, pass `true` (indicating it’s a left child).  
   - For the **right child**, pass `false` (not a left child).  

---

## ⏱️ Complexity Analysis
- **Time Complexity:** `O(n)`  
  Every node is visited once, where `n` is the number of nodes in the tree.  

- **Space Complexity:** `O(h)`  
  Where `h` is the height of the tree (recursion stack).  
  - Worst case (unbalanced tree): `O(n)`  
  - Best case (balanced tree): `O(log n)`  

---

## 💻 Code Implementation (Java)
```java
public class TreeNode {
    int val;
    TreeNode left;
    TreeNode right;
    TreeNode(int x) { 
        val = x; 
    }
}

class Solution {
    public int sumOfLeftLeaves(TreeNode root) {
        return dfs(root, false);
    }

    private int dfs(TreeNode node, boolean isLeft) {
        if (node == null) return 0;
        if (node.left == null && node.right == null && isLeft) return node.val;
        return dfs(node.left, true) + dfs(node.right, false);
    }
}
