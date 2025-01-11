
# 📅 Day 61: 2024-10-10

## 🚀 Problems Solved

---

### 🧩 Problem 1: 
Write a recursive function that checks whether string A is a palindrome or Not.
Return 1 if the string A is a palindrome, else return 0.

Note: A palindrome is a string that's the same when read forward and backward.
- **Approach 1: Recursion**
  - *recursion, n/2 total calls stack size is n/2*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 1
public int solve(String A) {


  return isPalindrome(A, 0, A.length()-1);


}


int isPalindrome(String A, int i, int j){

  if(i >= j){
    return 1;
  }

  if(A.charAt(i) == A.charAt(j)){

    if(isPalindrome(A, i+1, j-1) == 1){
      return 1;
    }
    else{
      return 0;
    }
  }
  else{
    return 0;
  }

}

```

---

### 🧩 Problem 2: 
The Fibonacci numbers are the numbers in the following integer sequence.



0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 144, ……..

In mathematical terms, the sequence Fn of Fibonacci numbers is defined by the recurrence relation:

Fn = Fn-1 + Fn-2

Given a number A, find and return the Ath Fibonacci Number using recursion.

Given that F0 = 0 and F1 = 1.
- **Approach 1: Recursion**
  - *Imp here is to determine tc and sc, depth of tree is A, A levels, at each level 2 recurisive call , tree grows exponentially O(2^A) , spcace is at max stack size is A, max have A calls for the stack*
- **⏳ Time Complexity:** `O(2^A)`
- **💾 Space Complexity:** `O(A)`

```java
// Code implementation for Problem 2
public int findAthFibonacci(int A) {

  if(A == 0){
    return 0;
  }

  if(A == 1){
    return 1;
  }
  return findAthFibonacci(A-1) + findAthFibonacci(A-2);
}
```
---

### 🧩 Problem 3: 
Write a program to find the factorial of the given number A using recursion.

Note: The factorial of a number N is defined as the product of the numbers from 1 to N.

- **Approach 1: Recursion**
  - *TC and SC are imp, max no of calls is A, so tc is O(A) and max stack size possible is A, so O(A)*
- **⏳ Time Complexity:** `O(A)`
- **💾 Space Complexity:** `O(A)`

```java
// Code implementation for Problem 3
public int solve(int A) {
  if(A == 1){
    return 1;
  }

  return A * solve(A - 1);
}
```

---

