
# 📅 Day 50: 2024-09-29

## 🚀 Problems Solved

---

### 🧩 Problem 1: 
Let’s solve this problem step by step.

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






- **Approach 1: Bruteforce**
  - *Checkout yesterdays solutions, it's similar approach to it. Ans : RED *

---

### 🧩 Problem 2: 
A spider is trying to build a web for itself. The web built by it doubles every day.

If the spider entirely built the web in 15 days, how many days did it take for the spider to build 25% of the web?

Answer is an integer. Just put the number without any decimal places if it's an integer. If the answer is Infinity, output Infinity.

Feel free to get in touch with us if you have any questions

- **Approach:**
  - *The key to solving this problem lies in understanding the doubling nature of the web growth. The web doubles in size every day, and it takes 15 days to reach full size. We're asked to determine how long it took to build 25% of the web.

Conceptual Analysis:
Since the web doubles in size every day, the amount of web on day n is twice the amount on day n - 1.
Let's think backwards from day 15, when the web is completely built.
Step-by-Step Backward Calculation:
On day 15, the web is 100% complete.
On day 14, the web must have been 50% complete (since it doubled on day 15).
On day 13, the web must have been 25% complete (since it doubled on day 14).
Conclusion:
It took the spider 13 days to build 25% of the web.*

---

### 🧩 Problem 3: 
Given an integer array A of size N. Return 1 if the array can be arranged to form an arithmetic progression, otherwise return 0.

A sequence of numbers is called an arithmetic progression if the difference between any two consecutive elements is the same.
- **Approach 1: Bruteforce**
  - *Bruteforce thinking & optimized soln as well*
- **⏳ Time Complexity:** `O(nlogn+n)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 3
public int solve(int[] A) {
  Arrays.sort(A);
  int diff = Math.abs(A[0]-A[1]);

  for(int i = 1; i < A.length; i++){
    int temp_diff = Math.abs(A[i]-A[i-1]);
    if(temp_diff != diff){
      return 0;
    }
  }
  return 1;
}
```

---

