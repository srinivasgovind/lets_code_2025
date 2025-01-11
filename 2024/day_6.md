
# 📅 Day 6: 2024-08-16

## 🚀 Problems Solved

---

### 🧩 Problem 1: Equilibrium Index
- **Approach 1: Prefix**
  - * Use prefix array to get left sum or right sum in constant time*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 1
public int solve(int[] A) {
  int n = A.length;
  int[] prefix = new int[n];

  prefix[0] = A[0];
  for(int i = 1; i < n; i++){
    prefix[i] = prefix[i-1] + A[i];
  }

  for(int i = 0; i <n; i++){
    int sl = 0; int sr=0;

    if(i == 0){
      sl= 0;
      sr = prefix[n-1] - prefix[i];
    }
    else if(i == n-1){
      sl = prefix[i-1];
      sr = 0;
    }
    else{
      sl = prefix[i-1];
      sr = prefix[n-1] - prefix[i];
    }
    if(sl == sr){
      return i;
    }
  }
  return -1;
}
```

- **Approach 2:**
  - * Oberservation and eliminate prefix array*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 1
public int solve(int[] A) {
  int n = A.length;
  int[] prefix = new int[n];

  int totalsum = 0;
  for(int i = 0; i < n; i++){
    totalsum += A[i];
  }

  int currentSum = 0;
  for(int i = 0; i <n; i++){
    int sl = 0; int sr=0; currentSum += A[i];

    if(i == 0){
      sl= 0;
      sr = totalsum - currentSum;
    }
    else if(i == n-1){
      sl = currentSum - A[i];
      sr = 0;
    }
    else{
      sl = currentSum - A[i];
      sr = totalsum - currentSum;
    }
    if(sl == sr){
      return i;
    }
  }
  return -1;
}
```
- **Approach 3:**
  - * Observation and reduce complexity*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 1
public int solve(int[] A) {
  int n = A.length;
  int[] prefix = new int[n];

  int totalSum = 0;
  for(int i = 0; i < n; i++){
    totalSum += A[i];
  }
  int sum1 = 0;
  for(int i = 0; i <n; i++){
    totalSum -= A[i];
    if(sum1 == totalSum){
      return i;
    }
    sum1 += A[i];
  }
  return -1;
}
```
---

### 🧩 Problem 2: Special Index (count special indexes, ith index becomes special index, where remove ith index then sum of even == sum of odd)
- **Approach:**
  - * Maintain even prefix and odd prefix and think about toggling of indexes after removal of any index*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 2
public int solve(int[] A) {

  int n = A.length;
  int count = 0;
  int evenPrefix[] = new int[n];
  int oddPrefix[] = new int[n];

  evenPrefix[0] = A[0];
  oddPrefix[0] = 0;
  for(int i = 1; i < n; i++){
    if(i % 2 == 0){
      evenPrefix[i] = evenPrefix[i-1] + A[i];
      oddPrefix[i] = oddPrefix[i-1] + 0;
    }else{
      evenPrefix[i] = evenPrefix[i-1] + 0;
      oddPrefix[i] = oddPrefix[i-1] + A[i];
    }
  }

  for(int i = 0; i< n; i++){
    int sumEven = 0;
    int sumOdd = 0;

    if(i > 0){
      sumEven = evenPrefix[i-1];
      sumOdd = oddPrefix[i-1];
    }

    sumEven += oddPrefix[n-1] - oddPrefix[i];
    sumOdd += evenPrefix[n-1] - evenPrefix[i];


    if(sumEven == sumOdd){
      count++;
    }
  }
  return count;

}
```                                                             
---

