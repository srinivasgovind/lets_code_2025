
# 📅 Day 35: 2024-09-14

## 🚀 Problems Solved

---

### 🧩 Problem 1: 
You are given an integer array A of length N comprising of 0's & 1's, and an integer B.

You have to tell all the indices of array A that can act as a center of 2 * B + 1 length 0-1 alternating subarray.

A 0-1 alternating array is an array containing only 0's & 1's, and having no adjacent 0's or 1's. For e.g. arrays [0, 1, 0, 1], [1, 0] and [1] are 0-1 alternating, while [1, 1] and [0, 1, 0, 0, 1] are not.
- **Approach 1: Bruteforce**
  - *[Briefly describe your approach]*
- **⏳ Time Complexity:** `O((n-window+1)*(window))`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 1
public int[] solve(int[] A, int B) {

  int window = 2 * B + 1;
  List<Integer> ans = new ArrayList<>();
  for(int i = 0; i < A.length - window+1; i++){
    boolean flag = true;
    int prev = -1;

    for(int j = i; j < i+window; j++){
      if(A[j] == prev){
        flag = false;
        break;
      }
      prev = A[j];
    }
    if(flag){
      ans.add(i+B);
    }
  }

  int result[] = new int[ans.size()];
  for(int i=0; i<ans.size(); i++){
    result[i] = ans.get(i);
  }
  return result;
}
```

---

### 🧩 Problem 2: 
You are given two matrices A & B of same size, you have to return another matrix which is the sum of A and B.
Note: Matrices are of same size means the number of rows and number of columns of both matrices are equal.
- **Approach 1: Bruteforce**
  - *Bruteforce way*
- **⏳ Time Complexity:** `O(n^2)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 2
public int[][] solve(int[][] A, int[][] B) {

  int[][] result = new int[A.length][A[0].length];

  for(int i = 0; i < A.length; i++){
    for(int j = 0; j < A[0].length; j++){
      result[i][j] = A[i][j] + B[i][j];
    }
  }
  return result;
}
```
---

### 🧩 Problem 3: 
Give a N * N square matrix A, return an array of its anti-diagonals. Look at the example for more details.
input
1 2 3
4 5 6
7 8 9

output
1 0 0
2 4 0
3 5 7
6 8 0
9 0 0
- **Approach 1: Bruteforce**
  - *[Briefly describe your approach]*
- **⏳ Time Complexity:** `O(n^2)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 3
public int[][] diagonal(int[][] A) {
  int n = A.length;
  int [][] result = new int [2*n-1][n];

  int x=0;
  int y= 0;

  for(int j =0; j < n; j++){
    int i = 0;
    int k = j;
    y = 0;
    while(i < n && k >= 0){
      result[x][y] = A[i][k];
      y++;
      i++;
      k--;
    }
    x++;
  }

  for(int i =1; i < n; i++){
    int j= n-1; int k = i; y=0;
    while(j>=0 && k < n){
      result[x][y] = A[k][j];
      k++; j--;
      y++;
    }
    x++;
  }
  return result;
}
```

---

