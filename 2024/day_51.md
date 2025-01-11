
# 📅 Day 51: 2024-09-30

## 🚀 Problems Solved

---

### 🧩 Problem 1: 
Given an integer array A, find if an integer p exists in the array such that the number of integers greater than p in the array equals p.
- **Approach 1: Bruteforce**
  - *All combinations*
- **⏳ Time Complexity:** `O(n^2)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 1
public int solve(int[] A) {

  int n = A.length;

  for(int i = 0; i < A.length; i++){

    int current = A[i];
    int greaterCount = 0;


    for(int j = 0; j < A.length; j++){
      if(A[j] > current){
        greaterCount++;
      }
    }
    if(current == greaterCount){
      return 1;
    }

  }
  return -1;
  
}
```

- **Approach 2: Optimized**
  - *sort the array , so you can get no of elements less than it easily*
- **⏳ Time Complexity:** `O(nlogn+n)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 1
public int solve(int[] A) {

  Integer[] array = Arrays.stream(A).boxed().toArray(Integer[]::new);
  Arrays.sort(array, Collections.reverseOrder());
  int count = 0;
  int greater = 0;

  if(array[0] == 0){
    return 1;
  }


  for(int i = 1; i < array.length; i++){
    if(array[i] != array[i-1]){
      greater = i;
    }

    if(array[i] == greater){
      return 1;
    }
  }

  return -1;

}
```

---

### 🧩 Problem 2: 
Given an array with N objects colored red, white, or blue, sort them so that objects of the same color are adjacent, with the colors in the order red, white, and blue.

We will represent the colors as,

red -> 0
white -> 1
blue -> 2

Note: Using the library sort function is not allowed.
- **Approach 1: Bruteforce**
  - *Bubble Sort*
- **⏳ Time Complexity:** `O(n^2)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 2
public int[] sortColors(int[] A) {

  //bubble sort
  for(int i = 0; i < A.length; i++){

    for(int j = i+1; j < A.length; j++){

      if(A[i] > A[j]){
        int temp = A[i];
        A[i] = A[j];
        A[j] = temp;
      }
    }
  }

  return A;
}
```

- **Approach 2: Optimized**
  - *We have only 3 colors, think*
- **⏳ Time Complexity:** `O(n+n)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 2
public int[] sortColors(int[] A) {

  int zeroCount = 0;
  int oneCount = 0;
  int twoCount = 0;

  for(int i = 0; i < A.length; i++){

    if(A[i] == 0){
      zeroCount++;
    }
    else if(A[i] == 1){
      oneCount++;
    }else{
      twoCount++;
    }
  }
  int ptr = 0;
  while(zeroCount > 0){
    A[ptr] = 0;
    ptr++;
    zeroCount--;
  }


  while(oneCount > 0){
    A[ptr] = 1;
    ptr++;
    oneCount--;
  }


  while(twoCount > 0){
    A[ptr] = 2;
    ptr++;
    twoCount--;
  }


  return A;
}
```
- **Approach 3: Dutch National Algorithm**
  - *Hard Algo, please do multiple dry runs to get this algo*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 2
public int[] sortColors(int[] A) {

  int low = 0;
  int mid = 0;
  int high = A.length - 1;

  while(mid <= high){

    if(A[mid] == 0){
      int temp = A[low];
      A[low] = A[mid];
      A[mid] = temp;
      low++;
      mid++;
    }
    else if(A[mid] == 1){
      mid++;
    }
    else{
      int temp = A[mid];
      A[mid] = A[high];
      A[high] = temp;
      high--;
    }
  }
  return A;
}
```
---

### 🧩 Problem 3:
Given an integer array A of size N. You can remove any element from the array in one operation.
The cost of this operation is the sum of all elements in the array present before this operation.

Find the minimum cost to remove all elements from the array.
- **Approach 2: Optimized**
  - *calcualte the formual for [a,b,c,d] array*
- **⏳ Time Complexity:** `O(nlogn + n)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 3
public int solve(int[] A) {

  Arrays.sort(A);
  int cost = 0;

  for(int i =A.length-1; i >= 0; i--){
    cost += (A.length-i) * A[i];
  }
  return cost;
}
```

---

