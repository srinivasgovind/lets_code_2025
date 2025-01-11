
# 📅 Day 66: 2024-10-15

## 🚀 Problems Solved

---

### 🧩 Problem 1: 
Given a binary tree, return the preorder traversal of its nodes values.
- **Approach 1: Bruteforce**
  - *Recursive approach*
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
  public int[] preorderTraversal(TreeNode A) {

    ArrayList<Integer> list=new ArrayList<>();
    preorderTraversalHelper(A,list);
    int res[]=new int[list.size()];
    for(int i=0;i<list.size();i++){
      res[i]=list.get(i);
    }
    return res;
  }
  void preorderTraversalHelper(TreeNode A,ArrayList<Integer> list){
    if(A==null){
      return;
    }
    list.add(A.val);
    preorderTraversalHelper(A.left,list);
    preorderTraversalHelper(A.right,list);
  }
}
```

- **Approach 2: Optimized**
  - *Iterative approach*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 1
public class Solution {
  public int[] preorderTraversal(TreeNode A) {

    ArrayList<Integer> list=new ArrayList<>();
    Stack<TreeNode> stack = new Stack<>();

    stack.push(A);
    TreeNode current = null;
    while(!stack.isEmpty()){
      current = stack.pop();

      list.add(current.val);
      if(current.right != null){
        stack.push(current.right);
      }
      if(current.left != null){
        stack.push(current.left);
      }

    }

    int[] arrAns = new int[list.size()];

    for(int i = 0; i < list.size(); i++){
      arrAns[i] = list.get(i);
    }
    return arrAns;
  }

}
```

---

### 🧩 Problem 2: 
Given a binary tree, return the Postorder traversal of its nodes values.
- **Approach 1: Bruteforce**
  - *Recursion*
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
  public int[] postorderTraversal(TreeNode A) {
    ArrayList<Integer> list=new ArrayList<>();
    postorderTraversalHelper(A,list);
    int result[]=new int[list.size()];
    for(int i=0;i<list.size();i++){
      result[i]=list.get(i);
    }
    return result;
  }

  void postorderTraversalHelper(TreeNode A,ArrayList<Integer> list){
    if(A==null){
      return;
    }
    postorderTraversalHelper(A.left,list);
    postorderTraversalHelper(A.right,list);
    list.add(A.val);
  }
}
```

- **Approach 2: Optimized**
  - *Iterative approach*
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
  public int[] postorderTraversal(TreeNode A) {
    ArrayList<Integer> list=new ArrayList<>();
    Stack<TreeNode> stack = new Stack<>();
    Stack<Integer> stack2= new Stack<>();
    stack.push(A);
    while(!stack.isEmpty()){
      TreeNode current = stack.pop();

      stack2.push(current.val);

      if(current.left != null){
        stack.push(current.left);
      }
      if(current.right != null){
        stack.push(current.right);
      }




    }

    int result[]=new int[stack2.size()];
    int ptr =0;
    while(!stack2.isEmpty()){
      result[ptr]=stack2.pop();
      ptr++;
    }
    return result;
  }
}

```

---

### 🧩 Problem 3: 
You are given the root node of a binary tree A. You have to find the height of the given tree.

A binary tree's height is the number of nodes along the longest path from the root node down to the farthest leaf node.
- **Approach 1: Bruteforce**
  - *Recursive*
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
  public int solve(TreeNode A) {

    if(A == null){
      return 0;
    }
    int leftTree = solve(A.left);
    int rightTree = solve(A.right);

    return Math.max(leftTree, rightTree) +1;
  }



}
```
---

