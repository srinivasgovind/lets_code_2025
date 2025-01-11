
# 📅 Day 40: 2024-09-19

## 🚀 Problems Solved

---

### 🧩 Problem 1: 
You are given an array A consisting of heights of Christmas trees and an array B of the same size consisting of the cost of each of the trees (Bi is the cost of tree Ai, where 1 ≤ i ≤ size(A)), and you are supposed to choose 3 trees (let's say, indices p, q, and r), such that Ap < Aq < Ar, where p < q < r.
The cost of these trees is Bp + Bq + Br.

You are to choose 3 trees such that their total cost is minimum. Return that cost.

If it is not possible to choose 3 such trees return -1.
- **Approach 1: Bruteforce**
  - *Bruteforce way by iterating all possible pairs*
- **⏳ Time Complexity:** `O(n^3)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 1
public int solve(int[] A, int[] B) {

  int sum = Integer.MAX_VALUE;

  for(int i = 0; i < A.length; i++){
    for(int j = i+1; j < A.length; j++){
      for(int k = j+1; k < A.length; k++){
        if(A[i] < A[j] && A[j] < A[k]){
          sum = Math.min(sum, B[i]+B[j]+B[k]);
        }
      }
    }
  }
  if(sum == Integer.MAX_VALUE){
    return -1;
  }
  return sum;
}

```

- **Approach 2: Optimized**
  - *take j as middle value iterate left to find i and iterate right to find k*
- **⏳ Time Complexity:** `O(n^2)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 1
public int solve(int[] A, int[] B) {

  int min_cost = (int)(1e9 + 10);

  for(int j = 1; j < A.length - 1; j++){

    int min_i = (int)(1e9 + 10);
    int min_k = (int)(1e9 + 10);
    for(int i = j-1;  i>=0; i--){
      if(A[i]<A[j] && B[i]<min_i){
        min_i = B[i];

      }
    }

    for(int k = j+1; k < A.length; k++){
      if(A[j] < A[k] && B[k] < min_k){
        min_k = B[k];
      }
    }
    min_cost = Math.min(min_cost, B[j]+min_i+min_k);
  }
  if(min_cost == (int)(1e9 + 10)){
    return -1;
  }

  return min_cost;

}
```

---

### 🧩 Problem 2: 
Given an array of integers A, of size N.

Return the maximum size subarray of A having only non-negative elements. If there are more than one such subarray, return the one having the smallest starting index in A.

NOTE: It is guaranteed that an answer always exists.
- **Approach 1: Bruteforce**
  - *Bruteforce way by iterating all subarrays*
- **⏳ Time Complexity:** `O(n^3)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 2
public int[] solve(int[] A) {
  List<Integer> arrayList = new ArrayList<>();
  int maxlength = 0;
  int start = 0;
  int end = 0;
  for(int i  = 0; i < A.length; i++){
    for(int j = i; j<A.length; j++){
      int flag = 0;
      for(int k = i; k <= j; k++){
        if(A[k] < 0){
          flag = 1;
          break;
        }
      }
      if(flag == 0 && j-i+1 > maxlength){
        start = i;
        end  = j;
        maxlength = j-i+1;
      }

    }

  }
  int result[] = new int[maxlength];
  int ptr = 0;
  for(int i = start; i <=end; i++){
    result[ptr] = A[i];
    ptr++;
  }
  return result;
}
```

- **Approach 2: Optimized**
  - * using pointers, when negative number comes, drop existing i and j and start fresh*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 2
public int[] solve(int[] A) {
  int maxlength = 0;
  int start = 0;
  int end = 0;
  int i = 0;
  int j = 0;
  while(i < A.length && j < A.length){

    if(A[j]>0){
      j++;
    }
    else{

      if(j-i > maxlength){
        start = i;
        end  = j-1;
        maxlength = j-i;
      }
      i = j+1;
      j++;

    }

  }
  if(j-i > maxlength){
    start = i;
    end  = j-1;
    maxlength = j-i;
  }

  int result[] = new int[maxlength];
  int ptr = 0;
  for(int k = start; k<=end; k++){
    result[ptr] = A[k];
    ptr++;
  }
  return result;
}
```

---

### 🧩 Problem 3: 
************
*****  *****
****    ****
***      ***
**        **
*          *
*          *
**        **
***      ***
****    ****
*****  *****
************
- **Approach 1: Bruteforce**
  - *Bruteforce way*
- **⏳ Time Complexity:** `O(n^2)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 3
public static void main(String[] args) {
  // YOUR CODE GOES HERE
  // Please take input and print output to standard input/output (stdin/stdout)
  // DO NOT USE ARGUMENTS FOR INPUTS
  // E.g. 'Scanner' for input & 'System.out' for output
  Scanner sc = new Scanner(System.in);
  int n = sc.nextInt();
  for(int i = n; i>=1; i--){
    int noofspaces = n*2 - i*2;
    for(int j = 1; j <=i; j++){
      System.out.print("*");
    }
    for(int j=1; j<=noofspaces; j++){
      System.out.print(" ");
    }
    for(int j = 1; j <=i; j++){
      System.out.print("*");
    }
    System.out.println();
  }

  for(int i = 1; i<=n; i++){
    int noofspaces = n*2 - i*2;
    for(int j = 1; j <=i; j++){
      System.out.print("*");
    }
    for(int j=1; j<=noofspaces; j++){
      System.out.print(" ");
    }
    for(int j = 1; j <=i; j++){
      System.out.print("*");
    }
    System.out.println();
  }

}
```

---

