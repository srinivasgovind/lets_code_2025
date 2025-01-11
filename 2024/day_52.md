
# 📅 Day 52: 2024-10-01

## 🚀 Problems Solved

---

### 🧩 Problem 1: toLower()
- **Approach 1: Bruteforce**
  - *Bruteforce thinking*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 1
public char[] to_lower(char[] A) {

  for(int i = 0; i < A.length; i++){
    if(A[i] >= 65 && A[i] <= 90){
      A[i] += 32;
    }
  }
  return A;
}
```
---

### 🧩 Problem 2: toUpper()
- **Approach 1: Bruteforce**
  - *Bruteforce way*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 2
public char[] to_upper(char[] A) {
  for(int i = 0; i < A.length; i++){

    if(A[i] >= 97 && A[i] <= 122){
      A[i] = (char)(A[i] - 32);
    }
  }
  return A;
}
}
```
---

### 🧩 Problem 3: isAlpha
- **Approach 1: Bruteforce**
  - *Bruteforce way*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 3
public int solve(char[] A) {
  for(int i = 0; i < A.length; i++){
    if(!(A[i] >= 65 && A[i] <= 90 || A[i] >= 97 && A[i] <= 122 || A[i] >= 48 && A[i] <= 57)){
      return 0;
    }
  }
  return 1;
}
```
---

