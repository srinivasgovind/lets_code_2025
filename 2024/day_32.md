
# 📅 Day 32: 2024-09-11

## 🚀 Problems Solved

---

### 🧩 Problem 1: 
You are given a string S, and you have to find all the amazing substrings of S.

An amazing Substring is one that starts with a vowel (a, e, i, o, u, A, E, I, O, U).

Input
- **Approach:**
  - *Bruteforce Way, getting TLE Exceeded*
- **⏳ Time Complexity:** `O(n^2)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 1
public int solve(String A) {
  int n = A.length();
  int count = 0;
  for(int i = 0; i < n; i++){
    char ch = A.charAt(i);
    if(ch == 'a' || ch == 'e' || ch == 'i' || ch == 'o' || ch == 'u' || ch == 'A' || ch == 'E' || ch == 'I' || ch == 'O' || ch == 'U'){
      count +=1;
      count %= 10003;
      for(int j = i + 1; j < n; j++){
        count++;
        count %= 10003;
      }
    }
  }
  return count;
}
```
- **Approach: Optimized**
  - *Carry Backward*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 1
public int solve(String A) {
  int n = A.length();
  int count = 0;
  int len = 0;
  for(int i = n-1; i >= 0; i--){
    len++;
    char ch = A.charAt(i);
    if(ch == 'a' || ch == 'e' || ch == 'i' || ch == 'o' || ch == 'u' || ch == 'A' || ch == 'E' || ch == 'I' || ch == 'O' || ch == 'U'){
      count +=len;
      count %= 10003;
    }
  }
  return count;
}
```

---

### 🧩 Problem 2:
You are given an integer array A.

Decide whether it is possible to divide the array into one or more subarrays of even length such that the first and last element of all subarrays will be even.

Return "YES" if it is possible; otherwise, return "NO" (without quotes).
- **Approach:**
  - *Observation*
- **⏳ Time Complexity:** `O(1)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 2
public String solve(int[] A) {
  int n = A.length;

  if(n % 2 == 0 && A[0] %2 == 0 && A[n-1] %2 == 0){
    return "YES";

  }
  return "NO";
}
```

---

### 🧩 Problem 3: 
Given an integer array A containing N distinct integers, you have to find all the leaders in array A. An element is a leader if it is strictly greater than all the elements to its right side.
- **Approach:**
  - *Your brain know bruteforce, ask him*
- **⏳ Time Complexity:** `O(n^2)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 3
[Write your Java code here]
```
- **Approach: Optimized**
  - *Carry Forward*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 3
public ArrayList<Integer> solve(ArrayList<Integer> A) {
  int n = A.size();
  ArrayList<Integer> ans = new ArrayList<>();
  int maxSoFar = A.get(n - 1);
  ans.add(A.get(n - 1));
  for(int i = A.size() - 2; i >= 0; i--){
    if(A.get(i) > maxSoFar){
      ans.add(A.get(i));
      maxSoFar = A.get(i);
    }
  }
  return ans;
}
```

---

