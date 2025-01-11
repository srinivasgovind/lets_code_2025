# 📅 Day 45: 2024-09-24

## 🚀 Problems Solved

---

### 🧩 Problem 1: 
 Given two integers A and B, find the greatest possible positive integer M, such that A % M = B % M.
- **Approach 1: Bruteforce**
  - *Solve Math LHS - RHS = 0*
- **⏳ Time Complexity:** `O(1)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 1
public int solve(int A, int B) {
  if(A > B){
    return A - B;
  }
  return B - A;
}
```

- **Approach 2: Optimized**
  - * No change just eliminate extra lines*
- **⏳ Time Complexity:** `O(1)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 1
public int solve(int A, int B) {
 return Math.abs(A-B);
}
```

---

### 🧩 Problem 2: 
You are given a number A in the form of a string. Check if the number is divisible by eight or not.

Return 1 if it is divisible by eight else, return 0.
- **Approach 1: Bruteforce**
  - *last 3 digits % 8*
- **⏳ Time Complexity:** `O(1)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 2
public int solve(String A) {
  int num = 0;
  int n = A.length();

  if(n == 1){
    num = A.charAt(0) - '0';
  }
  else if ( n == 2){
    num = (A.charAt(0) - '0') * 10 + (A.charAt(1) - '0');
  }
  else{
    num = (A.charAt(n-3) - '0') * 100 + (A.charAt(n - 2) - '0') * 10 + (A.charAt(n-1) - '0');
  }

  if(num % 8 == 0){
    return 1;
  }
  return 0;

}
```

---

### 🧩 Problem 3: 
You are given a large number in the form of a string A where each character denotes a digit of the number.
You are also given a number B. You have to find out the value of A % B and return it.
- **Approach 1: Bruteforce**
  - *formation of a number concept*
- **⏳ Time Complexity:** `O(len(A))`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 3
public int findMod(String A, int B) {

  long exp = 1;
  long result = 0;
  int n = A.length();

  for(int i = n - 1; i >= 0; i--){
    result = (result + ((A.charAt(i) - '0')%B * exp % B) % B) %B;
    exp = (exp * 10) % B;
  }
  return (int) result;
}
```

- **Approach 2: Optimized**
  - *No need extra mods*
- **⏳ Time Complexity:** `O(len(A))`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 3
public int findMod(String A, int B) {

  long exp = 1;
  long result = 0;
  int n = A.length();

  for(int i = n - 1; i >= 0; i--){
    result = (result + ((A.charAt(i) - '0') * exp) % B) %B;
    exp = (exp * 10) % B;
  }
  return (int) result;
}
```

---

