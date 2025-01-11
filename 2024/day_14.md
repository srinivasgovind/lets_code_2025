
# 📅 Day 14: 2024-08-24

## 🚀 Problems Solved

---

### 🧩 Problem 1: You are given an integer array A of size N. You have to perform B operations. In one operation, you can remove either the leftmost or the rightmost element of the array A. Find and return the maximum possible sum of the B elements that were removed after the B operations.
- **Approach:**
  - * Prefix and Suffix *
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 1
public int solve(int[] A, int B) {

  int prefix[] = new int[A.length];
  int suffix[] = new int[A.length];

  prefix[0] = A[0];
  suffix[A.length - 1] = A[A.length - 1];

  for(int i = 1; i < A.length; i++){
    prefix[i] = prefix[i-1] + A[i];
  }

  for(int i = A.length - 2; i >= 0 ; i--){
    suffix[i] = suffix[i+1] + A[i];
  }
  int globalMax = Integer.MIN_VALUE;

  for(int i = 0 ; i <= B ; i++){
    int leftsum = (i == 0) ? 0 : prefix[i-1];
    int rightsum = (i == B)? 0 : suffix[A.length - B + i];
    globalMax = Math.max(globalMax, leftsum + rightsum);
  }

  return globalMax;
}
```

---

### 🧩 Problem 2: Range Sum Query
- **Approach:**
  - * Use prefix array*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 2
public long[] rangeSum(int[] A, int[][] B) {

  long ans[] = new long[B.length];
  long prefix[] = new long[A.length];

  prefix[0] = A[0];

  for(int i = 1; i < A.length; i++){
    prefix[i] = prefix[i-1] + A[i];
  }

  for(int i = 0; i < B.length; i++){
    int left = B[i][0];
    int right = B[i][1];
    ans[i] = (left == 0) ? prefix[right] : prefix[right] - prefix[left - 1];
  }



  return ans;
}
```

---

