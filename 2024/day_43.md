
# 📅 Day 43: 2024-09-22

## 🚀 Problems Solved

---

### 🧩 Problem 1: 
Richard Hendricks, a mastermind in compression algorithms, is an employee of Hooli in Silicon Valley.
One day, he finally decided to quit and work on his new idea of the middle-out compression algorithm.

He needed to work at the bit - level to compress data. He, eventually, encountered this problem.
There is an array A of N integers. He has to perform certain operations on the elements.
In any one operation, two indices i and j (i < j) are chosen, and A[i] is replaced with A[i] & A[j],
and A[j] is replaced with A[i] | A[j], where & represents the Bitwise AND operation and | represents the Bitwise OR operation.
This operation is performed over all the pairs of integers in the array.

Help Richard find the Bitwise XOR of all the elements after performing the operations.
- **Approach 1: Bruteforce**
  - *[Briefly describe your approach]*
- **⏳ Time Complexity:** `O(n^2)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 1
[Write your Java code here]
```

- **Approach 2: Optimized**
  - *[Briefly describe your approach]*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 1
public int compressBits(int[] A) {

  int res = 0;
  for(int p = 0; p < A.length; p++){
    res ^= A[p];
  }
  return res;
}
```

---

### 🧩 Problem 2: 
Alex and Sam are good friends. Alex is doing a lot of programming these days. He has set a target score of A for himself.
Initially, Alex's score was zero. Alex can double his score by doing a question, or Alex can seek help from Sam for doing questions that will contribute 1 to Alex's score. Alex wants his score to be precisely A. Also, he does not want to take much help from Sam.

Find and return the minimum number of times Alex needs to take help from Sam to achieve a score of A.
- **Approach 1: Bruteforce**
  - *[Briefly describe your approach]*
- **⏳ Time Complexity:** `O(logA)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 2
public int solve(int A) {

  int count = 0;

  while(A > 0){
    if( (A & 1) == 1 ){
      count++;
    }
    A = A >> 1;
  }
  return count;
}
```

- **Approach 2: Optimized**
  - *[Briefly describe your approach]*
- **⏳ Time Complexity:** `O(1)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 2
public int solve(int A) {

  int count = 0;

  for(int i = 0; i < 32; i++){
    if((A & (1 << i)) != 0){
      count++;
    }
  }
  return count;
}
```

---

### 🧩 Problem 3: 
Alex has a cat named Boomer. He decides to put his cat to the test for eternity.

He starts on day 1 with one stash of food unit, every next day, the stash doubles.

If Boomer is well behaved during a particular day, only then she receives food worth equal to the stash produced on that day.

Boomer receives a net worth of A units of food. What is the number of days she received the stash?
- **Approach 1: Bruteforce**
  - *[Briefly describe your approach]*
- **⏳ Time Complexity:** `O(n^2)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 3
public int solve(int A) {

  int count = 0;

  while(A > 0){
    if( (A & 1) == 1 ){
      count++;
    }
    A = A >> 1;
  }
  return count;
}
```

- **Approach 2: Optimized**
  - *[Briefly describe your approach]*
- **⏳ Time Complexity:** `O(n^2)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 3
public int solve(int A) {

  int count = 0;

  for(int i = 0; i < 32; i++){
    if((A & (1 << i)) != 0){
      count++;
    }
  }
  return count;
}
```

---

