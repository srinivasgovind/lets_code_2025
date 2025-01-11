
# 📅 Day 5: 2024-08-15

## 🚀 Problems Solved

---

### 🧩 Problem 1: Product of Array Except Itself
- **Approach: Bruteforce**
  - Iterate through all pairs*
- **⏳ Time Complexity:** `O(n*n)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 1
public int[] productExceptSelf(int[] nums) {

  int result[] = new int[nums.length];

  for(int i = 0 ; i < nums.length; i++){
    int product = 1;
    for(int j = 0 ; j < nums.length; j++){
      if(i!=j){
        product *= nums[j];
      }
    }
    result[i] = product;
  }
  return result;
}
```

**Approach: Optimized 1**
- * Create Prefix and Postfix Arrays*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 1
public int[] productExceptSelf(int[] nums) {

  int[] prefix = new int[nums.length];
  int[] postfix = new int[nums.length];

  prefix[0] = nums[0];
  postfix[nums.length - 1] = nums[nums.length - 1];

  for(int i = 1; i < nums.length; i++){
    prefix[i] = prefix[i-1] * nums[i];
  }
  for(int i = nums.length - 2; i >= 0 ;i--){
    postfix[i] = postfix[i+1] * nums[i];
  }
  int[] result = new int[nums.length];

  for(int i = 0 ; i < nums.length; i++){
    if(i == 0){
      result[i] = postfix[i+1];
    }
    else if(i == nums.length-1){
      result[i] = prefix[i-1];
    }
    else{
      result[i] = prefix[i-1] * postfix[i+1];
    }
  }
  return result;

}
```
**Approach: Optimized 2**
- *Create Left product and Right product*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 1
public int[] productExceptSelf(int[] nums) {

  int[] result = new int[nums.length];
  int[] leftproduct = new int[nums.length];
  int[] rightproduct = new int[nums.length];

  leftproduct[0] = 1;
  rightproduct[nums.length -1] = 1;

  for(int i=1; i < nums.length; i++){
    leftproduct[i] = leftproduct[i-1] * nums[i-1];
  }

  for(int j = nums.length-2; j >= 0 ; j--){
    rightproduct[j] = rightproduct[j+1] * nums[j+1];
  }

  for(int i = 0; i < nums.length; i++){
    result[i] = leftproduct[i] * rightproduct[i];
  }

  return result;
}
```
**Approach: Optimized 3**
- *No need extra memory to maintain left and right array(tricky)*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 1
public int[] productExceptSelf(int[] nums) {

  int[] result = new int[nums.length];

  int leftprefix = 1;

  for(int i = 0; i < nums.length; i++){
    result[i] =  leftprefix;
    leftprefix *= nums[i];
  }
  int rightprefix = 1;
  for(int i = nums.length -1 ; i >= 0 ;i--){
    result[i] *= rightprefix;
    rightprefix *= nums[i];
  }

  return result;
}
```
---

