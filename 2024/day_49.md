
# 📅 Day 49: 2024-09-28

## 🚀 Problems Solved

---

### 🧩 Problem 1: 
You're given a read-only array of N integers. Find out if any integer occurs more than N/3 times in the array in linear time and constant additional space.
If so, return the integer. If not, return -1.

If there are multiple solutions, return any one.

Note: Read-only array means that the input array should not be modified in the process of solving the problem
- **Approach 1: Bruteforce**
  - *2 loops n^2 soln or sort the array nlogn soln*
- **⏳ Time Complexity:** `O(nlogn)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 1
public int repeatedNumber(int[] A) {
  int n = A.length;
  if (n == 0) {
    return -1;
  }

  // Step 1: Sort the array
  Arrays.sort(A);

  // Step 2: Check for an element that appears more than n/3 times
  int count = 1;
  int threshold = n / 3;

  for (int i = 1; i < n; i++) {
    if (A[i] == A[i - 1]) {
      count++;
    } else {
      count = 1; // Reset count when a new element appears
    }

    if (count > threshold) {
      return A[i];
    }
  }

  return -1; // If no element found that meets the criteria
}
```

- **Approach 2: Optimized**
  - *Boyer-Moore Voting Algorithm*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 1
public int repeatedNumber(int[] A) {

  int ele1 = -1;
  int freq1 = 0;

  int ele2 = -2;
  int freq2 = 0;

  for(int i = 0; i < A.length; i++){
    if(A[i] == ele1){
      freq1++;
    }
    else if(A[i] == ele2){
      freq2++;
    }
    else if(freq1 == 0){
      ele1 = A[i];
      freq1 = 1;
    }
    else if(freq2 == 0){
      ele2 = A[i];
      freq2 = 1;
    }
    else{
      freq1--;
      freq2--;
    }

  }
  int count1 = 0;
  int count2 = 0;

  for(int i = 0; i < A.length; i++){
    if(ele1 == A[i]){
      count1++;
    }
    else if(ele2 == A[i]){
      count2++;
    }
  }
  if(count1 > A.length/3){
    return ele1;
  }
  if(count2 > A.length/3){
    return ele2;
  }
  return -1;
}
```

---

### 🧩 Problem 2: 
Given an integer A, find and return the Ath magic number.

A magic number is defined as a number that can be expressed as a power of 5 or a sum of unique powers of 5.

First few magic numbers are 5, 25, 30(5 + 25), 125, 130(125 + 5), ….
- **Approach 1: Bruteforce**
  - *Tricky needs observation by writing A: 1 to 10 results and observe*
- **⏳ Time Complexity:** `O(n^2)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 2
public int solve(int A) {

  int result = 0;
  int ptr = 1;

  while( A != 0){
    int rem = A % 2;
    if(rem != 0){
      result += rem * Math.pow(5, ptr);
    }

    ptr++;
    A  = A/2;
  }
  return result;
}
```
---

### 🧩 Problem 3: 
You have 20 blue balls and 14 red balls in a bag. You put your hand in and remove 2 at a time.

If they’re of the same color, you add a blue ball to the bag.
If they’re of different colors, you add a red ball to the bag.
( Assume you have a big supply of blue & red balls for this purpose).

Note: When you take the two balls out, you don’t put them back in, so the number of balls in the bag keeps decreasing.

What will be the color of the last ball left in the bag?

- **Approach:**
  - Let’s solve this problem step by step.

Initial Configuration:
Blue Balls: 20
Red Balls: 14
Every time you take out two balls, the number of balls in the bag decreases by 1, and a new ball is added based on the color combination:

Same Color:

If you remove two blue balls, you add one blue ball.
If you remove two red balls, you add one blue ball.
Different Colors:

If you remove one blue and one red ball, you add one red ball.
Observations on Parity:
To determine the color of the last ball left in the bag, we can focus on the parity (odd/even) of the number of red balls.

Key Observations:
Only the red balls are added back when a red-blue pair is drawn, which means the number of red balls can change.
The blue balls are always added back when two of the same color are drawn.
Parity of Red Balls:
Initially, there are 14 red balls, which is an even number.
Every time you draw a blue-red pair, you remove one red ball and add a red ball back, meaning the total number of red balls remains unchanged.
Every time you draw two red balls, you reduce the number of red balls by 2, which also maintains the parity of the number of red balls.
Since the number of red balls starts as even and remains unchanged or reduced in even amounts, the parity of red balls will always be even throughout the process.

What Happens to Blue Balls:
The blue balls are manipulated in a way that eventually only one ball remains.
If there is an even number of red balls, there is no way to reduce the red balls to one because their parity remains even throughout. Therefore, the last remaining ball must be a blue ball.
Conclusion:
The last ball left in the bag will always be a blue ball.

Summary:
The number of red balls remains even throughout the process.
Since the number of red balls cannot be reduced to one (due to parity), the last remaining ball must be a blue ball.

---

