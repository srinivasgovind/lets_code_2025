
# 📅 Day 48: 2024-09-27

## 🚀 Problems Solved

---

### 🧩 Problem 1: 
Given an array of size N, find the majority element. The majority element is the element that appears more than floor(n/2) times.
You may assume that the array is non-empty and the majority element always exists in the array.
- **Approach 1: Bruteforce**
  - *2 Loops for all possibilites*
- **⏳ Time Complexity:** `O(n^2)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 1
public int majorityElement(int[] A) {
  int n = A.length;

  for (int i = 0; i < n; i++) {
    int count = 0;

    // Count occurrences of A[i]
    for (int j = 0; j < n; j++) {
      if (A[j] == A[i]) {
        count++;
      }
    }

    // Check if the current element is the majority element
    if (count > n / 2) {
      return A[i];
    }
  }

  // Return 0 or an error if no majority element is found (although a majority element is guaranteed)
  return 0;
}

```

- **Approach 2: Optimized**
  - *[Briefly describe your approach]*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 1
public int majorityElement(final int[] A) {

  int ele = A[0];
  int freq = 1;

  for(int i = 1; i < A.length; i++){

    if(freq == 0){
      ele = A[i];
      freq = 1;
    }
    else if (ele == A[i]){
      freq++;
    }
    else if(ele != A[i]){
      freq--;
    }
  }
  // Step 2: Verify the candidate (optional in this case, since it is guaranteed to exist)
  // If the majority element is guaranteed to exist, below verification step is not strictly necessary.

  int count = 0;

  for(int i = 0; i < A.length; i++){
    if(A[i] == ele){
      count++;
    }
  }
  if(count > A.length/2){
    return ele;
  }

  return 0;
}
```

---

### 🧩 Problem 2: 
There are 100 doors, all closed. In a nearby cage are 100 monkeys.

The first monkey is let out and runs along the doors opening every one. The second monkey is then let out and runs along the doors closing the 2nd, 4th, 6th,… - all the even-numbered doors. The third monkey is let out. He attends only to the 3rd, 6th, 9th,… doors (every third door, in other words), closing any that is open and opening any that is closed, and so on. After all 100 monkeys have done their work in this way, what state are the doors in after the last pass?

Answer with the number of open doors.

Answer is an integer. Just put the number without any decimal places if it's an integer. If the answer is Infinity, output Infinity.

Feel free to get in touch with us if you have any questions
- **No problem! Let me explain in a simpler way.

### Problem Recap
- Imagine there are 100 doors, all initially closed.
- There are 100 monkeys, and each monkey takes a turn to "toggle" the doors.
- **Toggle** means: if the door is closed, the monkey opens it. If the door is open, the monkey closes it.

- Each monkey does the following:
  - The **1st monkey** opens all the doors.
  - The **2nd monkey** toggles every **2nd** door (door 2, 4, 6, 8, …).
  - The **3rd monkey** toggles every **3rd** door (door 3, 6, 9, 12, …).
  - And this continues until the **100th monkey**, who toggles only the **100th** door.

The question is: **How many doors are open at the end?**

### The Trick to Solving the Problem
The key to solving this problem is to think about how **many times each door is toggled**.

#### Step-by-Step Explanation:
1. **Each Door Gets Toggled Based on Its Number:**
  - A door is toggled whenever a monkey comes whose number is a **divisor** of the door number.
  - For example:
    - **Door 12** is toggled by monkeys 1, 2, 3, 4, 6, and 12 because these numbers are divisors of 12.

2. **Odd or Even Number of Toggles:**
  - Most doors are toggled an **even number of times**. This is because divisors usually come in **pairs**.
  - For example, door 12 is toggled 6 times, which is even.

3. **Perfect Squares Have Odd Number of Toggles:**
  - **Perfect squares** (like 1, 4, 9, 16, etc.) are special because they have an **odd** number of divisors.
  - For example:
    - **Door 9** has divisors 1, 3, 9. Notice that 3 appears twice as a divisor (it's paired with itself), which makes the total number of divisors **odd**.
  - Since these doors have an **odd number of toggles**, they will end up **open** at the end.

4. **Which Doors Are Perfect Squares?**
  - Between doors **1 to 100**, the doors that are perfect squares are:
    - 1, 4, 9, 16, 25, 36, 49, 64, 81, and 100.
  - There are **10** perfect squares between 1 and 100.

### Final Answer
- **Only the perfect square doors will be open at the end.**
- There are **10** perfect square doors between 1 and 100.
- Therefore, **10 doors** will be open.

### Summary
- Each door is toggled by the monkeys whose numbers are divisors of that door number.
- Most doors get toggled an even number of times and end up closed.
- Only the doors that are perfect squares have an odd number of divisors and end up open.
---

### 🧩 Problem 3:
One hundred people are standing in a circle in an order 1 to 100.

No.1 has a sword. He kills the next person (i.e., no. 2) and gives the sword to the next (i.e., no. 3). All person does the same until only one survives.

Which number survives at last?

Answer is an integer. Just put the number without any decimal places if it's an integer. If the answer is Infinity, output Infinity.

Feel free to get in touch with us if you have any questions
- **Approach 1**
  - *The problem you've described is a variation of the **Josephus problem**, specifically with every second person being killed.

In this problem:
- You have 100 people standing in a circle, numbered from 1 to 100.
- Starting with person 1, every second person is killed until only one remains.

### Solution to Josephus Problem:
For a Josephus problem where every second person is eliminated, there is a formula to determine the position of the last person remaining:

1. Find the **largest power of 2** that is less than or equal to `n` (in this case, `n = 100`).
2. Let this value be `L`.
3. The position of the last person is given by the formula:
   \[
   J(n) = 2 * (n - L) + 1
   \]
   where `n` is the total number of people, and `L` is the largest power of 2 less than or equal to `n`.

### Applying to Your Problem:
1. **Find the Largest Power of 2 ≤ 100**:
  - The largest power of 2 less than or equal to 100 is **64**.

2. **Calculate the Last Person Standing**:
   \[
   J(100) = 2 * (100 - 64) + 1 = 2 * 36 + 1 = 72 + 1 = 73
   \]

### Answer:
The number that survives at the end is **73**.

---

