
# 📅 Day 67: 2024-10-16

## 🚀 Problems Solved

---

### 🧩 Problem 1: 
You are given the root node of a binary tree A. You have to find the number of nodes in this tree.
- **Approach 1: Bruteforce**
  - *Left Subtree and Right Subtree concept helps to make subproblem for recursion*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 1
/**
 * Definition for binary tree
 * class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) {
 *      val = x;
 *      left=null;
 *      right=null;
 *     }
 * }
 */
public class Solution {
  public int solve(TreeNode A) {
    if(A == null){
      return 0;
    }
    int left_count = solve(A.left);
    int right_count = solve(A.right);
    return left_count + right_count + 1;
  }
}
```
---

### 🧩 Problem 2: 
Given the root of a tree A with each node having a certain value, find the count of nodes with more value than all its ancestors.

Ancestor means that every node that occurs before the current node in the path from root to the node.
- **Approach 1: Bruteforce**
  - *Recursive Way*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(n)`

```java
/**
 * Definition for binary tree
 * class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) {
 *      val = x;
 *      left=null;
 *      right=null;
 *     }
 * }
 */
public class Solution {
  public  int solve(TreeNode A) {

    TreeNode max_val = null ;

    return max_recursive(A, max_val);
  }

  int max_recursive(TreeNode A, TreeNode max_val){
    int max_count = 0;
    if(A == null){
      return 0;
    }
    if( max_val == null || A.val > max_val.val){
      max_count++;
      max_val = A;
    }

    int left_count = max_recursive(A.left, max_val);
    int right_count = max_recursive(A.right, max_val);
    return max_count + left_count + right_count;
  }
}

```
---

### 🧩 Problem 3: 
Given two binary trees, check if they are equal or not.

Two binary trees are considered equal if they are structurally identical and the nodes have the same value.
- **Approach 1: Bruteforce**
  - *Recursive Way, comparing current node, left subtree & right subtree*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 3
/**
 * Definition for binary tree
 * class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) {
 *      val = x;
 *      left=null;
 *      right=null;
 *     }
 * }
 */
public class Solution {
  public int isSameTree(TreeNode A, TreeNode B) {

    if(A == null && B == null){
      return 1;
    }
    else if(A == null || B == null){
      return 0;
    }

    if(A.val == B.val){
      if(isSameTree(A.left, B.left) == 1. && isSameTree(A.right, B.right) == 1){
        return 1;
      }
      else{
        return 0;
      }
    }

    return 0;
  }
}

```

- **Approach 2: Optimized**
  - *More Readable*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 3
/**
 * Definition for binary tree
 * class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) {
 *      val = x;
 *      left=null;
 *      right=null;
 *     }
 * }
 */
public class Solution {
  public int isSameTree(TreeNode A, TreeNode B) {

    if(A == null && B == null){
      return 1;
    }
    else if(A == null || B == null){
      return 0;
    }
    else if(A.val != B.val){
      return 0;
    }


    return isSameTree(A.left, B.left) & isSameTree(A.right, B.right);

  }
}
```

---

