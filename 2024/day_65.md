
# 📅 Day 65: 2024-10-14

## 🚀 Problems Solved

---

### 🧩 Problem 1: 
Given an expression string A, examine whether the pairs and the orders of “{“,”}”, ”(“,”)”, ”[“,”]” are correct in A.

Refer to the examples for more clarity.
- **Approach 1: Optimized**
  - *Stack famous qn*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 1
public int solve(String A) {

  Stack<Character> stack = new Stack<>();

  for(int i = 0; i < A.length(); i++){

    char ch = A.charAt(i);

    if(ch == '{' || ch == '[' || ch == '('){
      stack.push(ch);
      continue;
    }

    if(stack.isEmpty()){
      return 0;
    }

    if( ch == '}' && stack.peek() != '{'){
      return 0;
    }
    else if(ch == ']' && stack.peek() != '['){
      return 0;
    }
    else if(ch == ')' && stack.peek() != '('){
      return 0;
    }

    stack.pop();
  }

  return stack.isEmpty() ? 1 : 0;

}
```

- **Approach 2: Atlernative approach**
  - *Extra HashMap*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 1
public class Solution {
  public int solve(String A) {
    HashMap < Character, Character > mp = new HashMap < Character, Character > ();
    Stack < Character > st = new Stack < Character > ();
    mp.put(')', '(');
    mp.put('}', '{');
    mp.put(']', '[');
    for (int i = 0; i < A.length(); i++) {
      char c = A.charAt(i);
      if (c == '(' || c == '[' || c == '{') {
        // push any opening bracket into the stack
        st.push(c);
      } else if (st.empty() || st.peek() != mp.get(c)) {
        // check if the last unpaired opening bracket is of the same type 
        // as the current closing bracket
        return 0;
      } else {
        st.pop();
      }
    }
    // checks if all the opening brackets are paired
    if (st.empty())
      return 1;
    return 0;
  }
}
```

---

### 🧩 Problem 2: 
Design a stack that supports push, pop, top, and retrieve the minimum element in constant time.
push(x) -- Push element x onto stack.
pop() -- Removes the element on top of the stack.
top() -- Get the top element.
getMin() -- Retrieve the minimum element in the stack.
NOTE:
All the operations have to be constant time operations.
getMin() should return -1 if the stack is empty.
pop() should return nothing if the stack is empty.
top() should return -1 if the stack is empty.
- **Approach 1: Bruteforce**
  - *Here we're using inbuilt LinkedList to implement the Stack*
- **⏳ Time Complexity:** `O(1)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 2
class Solution {

  LinkedList<Integer> list = new LinkedList<>();
  LinkedList<Integer> minlist = new LinkedList<>();

  class Node{
    int value;
    int min;
    Node next;
    Node(int value){
      this.value = value;
    }
  }
  Node head = null;

  public void push(int x) {
    Node newnode = new Node(x);
    if(head == null){
      head = newnode;
      newnode.min = x;
      return;
    }
    newnode.next = head;
    if(x <= head.min){
      newnode.min = x;
    }else{
      newnode.min = head.min;
    }
    head = newnode;
  }

  public void pop() {
    if(head == null){
      return;
    }
    head = head.next;
  }

  public int top() {
    if(head == null){
      return -1;
    }
    return  head.value;
  }

  public int getMin() {

    if(head != null){
      return head.min;
    }
    return -1;
  }
}

```

- **Approach 2: Optimized**
  - *Every Method is O(1)*
- **⏳ Time Complexity:** `O(1)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 2
class Solution {

  class Node{
    int value;
    int min;
    Node next;
    Node(int value){
      this.value = value;
    }
  }
  Node head = null;

  public void push(int x) {
    Node newnode = new Node(x);
    if(head == null){
      head = newnode;
      newnode.min = x;
      return;
    }
    newnode.next = head;
    if(x <= head.min){
      newnode.min = x;
    }else{
      newnode.min = head.min;
    }
    head = newnode;
  }

  public void pop() {
    if(head == null){
      return;
    }
    head = head.next;
  }

  public int top() {
    if(head == null){
      return -1;
    }
    return  head.value;
  }

  public int getMin() {

    if(head != null){
      return head.min;
    }
    return -1;
  }
}
```

---

### 🧩 Problem 3: Given a binary tree, return the inorder traversal of its nodes' values.
- **Approach 1: Bruteforce**
  - *Recurison, [LDR], recall marriage example told in class :)*
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
  public int[] inorderTraversal(TreeNode A) {

    ArrayList<Integer> ans = new ArrayList<>();

    inorderTraversalHelper(A, ans);

    int[] ansArray = new int[ans.size()];

    for(int i = 0; i < ans.size(); i++){
      ansArray[i] = ans.get(i);
    }

    return ansArray;
  }

  public void inorderTraversalHelper(TreeNode A, ArrayList<Integer> ans){

    if(A == null){
      return;
    }
    inorderTraversalHelper(A.left, ans);
    ans.add(A.val);
    inorderTraversalHelper(A.right, ans);
  }
}

```

---

