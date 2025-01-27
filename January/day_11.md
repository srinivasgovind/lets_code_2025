
# 📅 Day 11: 2025-01-20

## What I Learned
- **Topic:**
- **Details:**
- **Streak Break Reason: No**

## 🚀 Problems Solved

---

### 🧩 Problem 1: 
Given an array of integers, every element appears thrice except for one, which occurs once.

Find that element that does not appear thrice.

NOTE: Your algorithm should have a linear runtime complexity.

Could you implement it without using extra memory?

- **Approach 2: Optimized**
  - *Understanding the array in bit wise, if we see bit wise table of the array, at any kth pos no_of_set_bits are multiples of 3 except the unqiue number.*
- **⏳ Time Complexity:** `O(n* 31)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 1
public int singleNumber(final int[] A) {

  int ans = 0;

  for(int i = 0; i <= 30; i++){
    //set bit count
    int count = 0;
    for(int j =0; j < A.length; j++){
      if((A[j] & (1 << i)) != 0){
        count++;
      }
    }
    count %= 3;
    ans += (count << i);
  }
  return ans;
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
  - *[Briefly describe your aproach]*
- **⏳ Time Complexity:** `O(n^2)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 3
[Write your Java code here]
```

---

