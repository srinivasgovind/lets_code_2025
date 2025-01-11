
# 📅 Day 7: 2024-08-17

## 🚀 Problems Solved

---

### 🧩 Problem 1: Valid Paranthesis
- **Approach:**
  - *Use Stack*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(n)`

```java
// Code implementation for Problem 1
public boolean isValid(String s) {

  Stack<Character> stack = new Stack<>();

  for(int i = 0; i<s.length(); i++){
    char ch = s.charAt(i);
    if(ch == '{' || ch == '[' || ch == '('){
      stack.push(ch);
      continue;
    }
    if(stack.isEmpty()){
      return false;
    }
    char peek = stack.peek();
    if((ch == '}' && peek == '{') || (ch == ']' && peek == '[') || (ch == ')' && peek == '(')){
      stack.pop();
    }
    else{
      return false;
    }
  }
  if(!stack.isEmpty()){
    return false;
  }
  return true;
}
```

---

