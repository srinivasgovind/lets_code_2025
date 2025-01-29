
# 📅 Day 12: 2025-01-21

## What I Learned
- **Topic:**
- **Details:**
- **Streak Break Reason: No**

## 🚀 Problems Solved

---

### 🧩 Problem 1: 
Given two integers A and B, find the greatest possible positive integer M, such that A % M = B % M.

- **Approach 2: Optimized**
  - *Explantion lies in comments of code*
- **⏳ Time Complexity:** `O(1)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 1
public int solve(int A, int B) {
  // a%m = b%m
  // a%m - b%m = 0
  // (a%m - b%m ) % m = 0 % m
  // (a-b) % m = 0
  // HERE M VALUES ARE FACTORS OF (A-B), M VALUES LIES IN [1, A-B]
  // QUESTION IS TO FIND MAXIMUM M VALUE, WHICH IS (A-B)


  return Math.abs(A - B);
}
```

---

### 🧩 Problem 2: [Problem Title or Description]
- **Approach 1: Bruteforce**
  - *[Briefly describe your approach]*
- **⏳ Time Complexity:** `O(n^2)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 2
[Write your Java code here]
```

- **Approach 2: Optimized**
  - *[Briefly describe your approach]*
- **⏳ Time Complexity:** `O(n^2)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 2
[Write your Java code here]
```

---

### 🧩 Problem 3: [Problem Title or Description]
- **Approach 1: Bruteforce**
  - *[Briefly describe your approach]*
- **⏳ Time Complexity:** `O(n^2)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 3
[Write your Java code here]
```

- **Approach 2: Optimized**
  - *[Briefly describe your approach]*
- **⏳ Time Complexity:** `O(n^2)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 3
[Write your Java code here]
```

---

