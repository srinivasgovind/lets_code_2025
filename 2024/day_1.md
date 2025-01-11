
# 📅 Day 1: 2024-08-11

## 🚀 Problems Solved

---

### 🧩 Problem 1: Is it a prime
- **Approach:**
  * Simple loop to check factors and a exit condition*
- **⏳ Time Complexity:** ` O(sqrt(n))`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 1

import java.util.Scanner;
Scanner sc = new Scanner(System.in);
int input = sc.nextInt();
boolean flag = true;
int i = 2;
while( i < input){
        if(input % 2 == 0){
            System.out.println("NO");
            flag = false;
            break;
        }
        i++;
}
if(flag){
    System.out.println("YES");
}
```

---

### 🧩 Problem 2: Is it perfect ( inputNumber == sum of all divisors except itself)
- **Approach:**
  - * Iterate over all the numbers if it's factor add to sum and do final check if n == sum*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 2
Scanner sc=new Scanner(System.in);
int noOfTestCases = sc.nextInt();
for(int cases = 0; cases < noOfTestCases; cases++){
    int n=sc.nextInt();

    int sum = 0;

        for(int i=1; i < n ;i++){
                if( n % i == 0){
                     sum += i;
                }

        }
        if(sum == n ){
        System.out. println("YES");
        }
        else{
            System.out.println("NO");
        }
}
```

---

### 🧩 Problem 3: Return Sqrt of a number
- **Approach:**
  - *Iterate through factors of A, write if cond to check*
- **⏳ Time Complexity:** `O(sqrt(A))`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 3
public int solve(int A) {

  for(int i = 1 ; i * i <= A ; i++){

    if(i * i == A){
      return i;
    }
  }
  return -1;
}
```

---

### 🧩 Problem 4: Amstrong Number from 1 to N
- **Approach:**
  - *Iterate, inner divide the number, cube it and compare with original*
- **⏳ Time Complexity:** `O(n * log10(n))`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 3
public void solve(int n) {

    for (int i = 1; i <= n; i++) {
        int icopy = i;
        int result = 0;
        while (icopy > 0) {
            int digit = icopy % 10;
            result += digit * digit * digit;
            icopy = icopy / 10;
        }
        if (result == i) {
            System.out.println(i);
        }
    }
}
```
---

### 🧩 Problem 4: Palindrome Number 
- **Approach 1:**
  - *Reverse a number and compare*
- **⏳ Time Complexity:** `O(log10(x))`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 3
public boolean isPalindrome(int x) {

  if( x < 0){
    return false;
  }
  int result = 0;
  int i = 0;
  int xcopy = x;
  while(xcopy > 0){
    int last_digit = xcopy % 10 ;
    result = result * 10 + last_digit;
    xcopy /= 10;
    i++;
  }

  if(result == x){
    return true;
  }
  return false;
}
```
- **Approach 2:**
  - *Reverse a half number and compare with orginal half*
  - *Number  ends with zero can never be a palindrome, if a number of digits is odd then middle should be ignored*
- **⏳ Time Complexity:** `O(log10(x)) or O(log10(x))/2`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 3
public boolean isPalindrome(int x) {
  if( x < 0 || (x > 0 && x % 10 == 0)){
    return false;
  }
  int reversed = 0;

  while(x > reversed){
    int last_digit = x % 10;
    reversed = reversed * 10 + last_digit;
    x = x/10;
  }
  return ( x == reversed || x == (reversed/10));
}
```
---