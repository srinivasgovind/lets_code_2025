
# 📅 Day 46: 2024-09-25

## 🚀 Problems Solved

---

### 🧩 Problem 1: 
Given a column title as appears in an Excel sheet, return its corresponding column number.
A -> 1
B -> 2
C -> 3
...
Z -> 26
AA -> 27
AB -> 28
- **Approach 1: Bruteforce**
  - *[Briefly describe your approach]*
- **⏳ Time Complexity:** `O(len(A))`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 1
public int titleToNumber(String A) {

  int result = 0;
  int n = A.length();
  for(int i = n - 1;  i >= 0; i--){
    int num = A.charAt(i) - 65 + 1;
    result += num * Math.pow(26, n-i-1);
  }
  return result;
}
```
---

### 🧩 Problem 2: 
Write a program to input an integer T and then for each test case input two integers A and B in two different lines and then print T lines containing Least Common Multiple (LCM) of two given 2 numbers A and B.

Note: LCM of two integers is the smallest positive integer divisible by both.

- **Approach 1: Bruteforce**
  - *Calculate LCM using the formula LCM(A, B) = (A * B) / GCD(A, B)*
- **⏳ Time Complexity:** `O(noOfCases * min(A, B))`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 2
public static void main(String[] args) {
  // YOUR CODE GOES HERE
  // Please take input and print output to standard input/output (stdin/stdout)
  // DO NOT USE ARGUMENTS FOR INPUTS
  // E.g. 'Scanner' for input & 'System.out' for output

  Scanner sc = new Scanner(System.in);

  int noOfCases = sc.nextInt();

  for(int i = 0; i < noOfCases; i++){

    int A = sc.nextInt();
    int B = sc.nextInt();

    int gcd = 1;

    for(int k = 1; k <= Math.min(A, B); k++){
      if( A % k == 0 && B % k == 0){
        gcd = k;
      }
    }
    System.out.println(A*B/gcd);
  }

}
```
---

### 🧩 Problem 3: 
Given an integer A representing a year, Return 1 if it is a leap year else, return 0.

A year is a leap year if the following conditions are satisfied:

The year is multiple of 400.
or the year is multiple of 4 and not multiple of 100.

- **Approach 1: Bruteforce**
  - *Kindergarden Logic*
- **⏳ Time Complexity:** `O(1)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 3
public int solve(int A) {

  if(A % 400 == 0 || ( A % 4 == 0 && A % 100 != 0)){
    return 1;
  }
  return 0;
}
```

---

