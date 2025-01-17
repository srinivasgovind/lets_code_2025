
# 📅 Day 6: 2025-01-15

## What I Learned
- **Topic: Arrays 2 & 3**
- **Details: ADV DSA**
- **Streak Break Reason: No**

## 🚀 Problems Solved

---

### 🧩 Problem 1: [Problem Title or Description]
- **Approach 1: Bruteforce**
  - *[Briefly describe your approach]*
- **⏳ Time Complexity:** `O(n^2)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 1
public int solve(int[] A) {

  //Find no of cycles exists, for every cycle swaps = cyclesize - 1 & add all swaps

  boolean[] visited = new boolean[A.length];
  int minswaps = 0;

  for(int i = 0; i < A.length; i++){
    if(A[i] == i || visited[i]){
      continue;
    }

    int current = i;
    int cycle_size = 0;
    while(!visited[current]){
      visited[current] = true;
      current = A[current];
      cycle_size++;
    }
    if(cycle_size > 1){
      minswaps += cycle_size -1;
    }
  }
  return minswaps;
}

```

- **Approach 2: Optimized**
  - *It's very tricky, need to solve again in free time.*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 1
public int solve(int[] A) {
    
    //Here instead of cycles finding we swap directly in the cycle 
  int swaps = 0;

  for(int i = 0; i < A.length; i++){
    if(A[i] == i){
      continue;
    }

    while(A[i] != i){
      int temp = A[i];
      A[i] = A[temp];
      A[temp] = temp;
      swaps++;
    }
  }
  return swaps;
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

