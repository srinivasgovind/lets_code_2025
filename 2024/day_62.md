
# 📅 Day 62: 2024-10-11

## 🚀 Problems Solved

---

### 🧩 Problem 1: 
Write a recursive function that takes a string, S, as input and prints the characters of S in reverse order.
- **Approach 1: Recursion**
  - *Here space is for data structure and stack, at max A no of calls*
- **⏳ Time Complexity:** `O(A)`
- **💾 Space Complexity:** `O(A)`

```java
// Code implementation for Problem 1
public static void main(String[] args) {
  // YOUR CODE GOES HERE
  // Please take input and print output to standard input/output (stdin/stdout)
  // DO NOT USE ARGUMENTS FOR INPUTS
  // E.g. 'Scanner' for input & 'System.out' for output
  Scanner sc = new Scanner(System.in);
  String A = sc.next();
  StringBuilder sb = new StringBuilder();
  reverse(A, 0, sb);
  System.out.println(sb.toString());



}

static void reverse(String A, int i , StringBuilder sb){

  if(i == A.length()-1){
    sb.append(A.charAt(A.length() - 1));
    return;
  }

  reverse(A, i+1, sb);

  sb.append(A.charAt(i));
  return;


} 
```

- **Approach 2: Optimized**
  - *Space dropped, now just stack space*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 1
public static void main(String[] args) {
  // YOUR CODE GOES HERE
  // Please take input and print output to standard input/output (stdin/stdout)
  // DO NOT USE ARGUMENTS FOR INPUTS
  // E.g. 'Scanner' for input & 'System.out' for output
  Scanner sc = new Scanner(System.in);
  String A = sc.next();
  reverse(A, 0);



}

static void reverse(String A, int i ){

  if(i == A.length()-1){
    System.out.print(A.charAt(A.length() - 1));
    return;
  }

  reverse(A, i+1);

  System.out.print(A.charAt(i));
  return;


} 
```

---

### 🧩 Problem 2: Given a number A, we need to find the sum of its digits using recursion.
- **Approach 1: Bruteforce**
  - *TC: O(log10(A)) and SC: also same A -> A/10 -> 1, another way its equal to (no of digits in A = log10(A)+1)*
- **⏳ Time Complexity:** `O(logA)`
- **💾 Space Complexity:** `O(logA)`

```java
// Code implementation for Problem 2
public int solve(int A) {
  if( A/10 == 0){
    return A;
  }
  return A % 10 + solve(A/10);
}
```
---

### 🧩 Problem 3: Solved Choose the correct  in Recursion 1 HW problems

---

