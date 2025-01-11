
# 📅 Day 68: 2024-10-17

## 🚀 Problems Solved

---

### 🧩 Problem 1: 
Given a binary tree, check whether it is a mirror of itself (i.e., symmetric around its center).
- **Approach 1: Bruteforce**
  - *Recursive call, look carefully how we compare oppisite directions*
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
  public int isSymmetric(TreeNode A) {

    return isSymmetricHelper(A.left, A.right);
  }

  int isSymmetricHelper(TreeNode A, TreeNode B){

    if(A == null && B == null){
      return 1;
    }
    if(A == null || B == null){
      return 0;
    }

    if(A.val != B.val){
      return 0;
    }

    return isSymmetricHelper(A.left, B.right) & isSymmetricHelper(A.right, B.left);
  }
}

```

- **Approach 2: Optimized**
- *More readable, optimized if conditions*
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
  public int isSymmetric(TreeNode A) {

    return isSymmetricHelper(A.left, A.right);
  }

  int isSymmetricHelper(TreeNode A, TreeNode B){

    if(A == null || B == null){
      return A == B ? 1 : 0;
    }

    if(A.val != B.val){
      return 0;
    }

    return isSymmetricHelper(A.left, B.right) & isSymmetricHelper(A.right, B.left);
  }
}

```

---

### 🧩 Problem 2: 
Given a binary search tree of integers. You are given a range B and C.

Return the count of the number of nodes that lie in the given range.
- **Approach 1: Bruteforce**
  - *Recursive thinking, space O(n) in worst case for skewed trees*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 2
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
  public int solve(TreeNode A, int B, int C) {
    if(A == null){
      return 0;
    }
    int ans = 0;

    if(A.val >= B && A.val <= C){
      ans = 1;
    }

    return ans + solve(A.left, B, C) + solve(A.right, B, C);
  }
}

```
---

### 🧩 Problem 3: 
Given a binary tree A, invert the binary tree and return it.

Inverting refers to making the left child the right child and vice versa.
- **Approach 1: Bruteforce**
  - *Recursive thinking*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 3
public class Solution {
  public TreeNode invertTree(TreeNode A) {
    invertTreeHelper(A);
    return A;
  }
  void invertTreeHelper(TreeNode A){
    if(A==null){
      return;
    }
    TreeNode temp=A.left;
    A.left=A.right;
    A.right=temp;
    invertTree(A.left);
    invertTree(A.right);

  }
}
```

- **Approach 2: Optimized**
  - *More readable*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 3
// Code implementation for Problem 3
public TreeNode invertTree(TreeNode A) {
  if(A == null){
    return null;
  }
  TreeNode temp = invertTree(A.left);
  A.left = invertTree(A.right);
  A.right = temp;

  return A;
}
```

---

### 🧩 Problem 4:
Given a binary tree A, find the path from the root node to given B (For all test cases there will be a path).

- **Approach 1: Bruteforce**
  - *Recursive thinking*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(n)`

- **Approach 1: Optimized**
  - *More readable*
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
  public List<Integer> path = new ArrayList<>();
  public int[] solve(TreeNode A, int B) {
    findPath(A, B);
    return path.stream().mapToInt(i -> i).toArray();
  }

  boolean findPath(TreeNode root, int B){
    if(root == null){
      return false;
    }
    path.add(root.val);

    if(root.val == B){
      return true;
    }
    if(findPath(root.left, B) || findPath(root.right, B)){
      return true;
    }
    path.remove(path.size() -1);
    return false;
  }
}
```

---