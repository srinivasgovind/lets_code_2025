
# 📅 Day 38: 2024-09-17

## 🚀 Problems Solved

---

### 🧩 Problem 1: Minor Diagonal Sum
- **Approach 1: Bruteforce**
  - *Bruteforce way*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 1
public int solve(final int[][] A) {

  int sum = 0;
  int i = 0;
  int j = A[0].length - 1;

  while( i < A.length && j >= 0){
    sum += A[i][j];
    i++;
    j--;
  }
  return sum;
}
```
---

### 🧩 Problem 2: Are Matrices Same ?
- **Approach 1: Bruteforce**
  - *Bruteforce way*
- **⏳ Time Complexity:** `O(m*n)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 2
public int solve(int[][] A, int[][] B) {

  for(int i = 0; i < A.length; i++){
    for(int j = 0; j < A[0].length; j++){
      if(A[i][j] != B[i][j]){
        return 0;
      }
    }
  }
  return 1;
}
```

---

### 🧩 Problem 3: Matrix Scaler Product
- **Approach 1: Bruteforce**
  - *Bruteforce way*
- **⏳ Time Complexity:** `O(n*m)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 3
public int[][] solve(int[][] A, int B) {
  for(int i = 0; i < A.length; i++){
    for(int j = 0; j < A[0].length; j++){
      A[i][j] = A[i][j] * B;
    }
  }
  return A;
}
```

---

