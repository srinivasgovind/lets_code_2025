
# 📅 Day 10: 2024-08-20

## 🚀 Problems Solved

---

### 🧩 Problem 1: Mrege Two Sorted Lists
- **Approach 1:**
  - *Iterative approach*
- **⏳ Time Complexity:** `O(n)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 1
public ListNode mergeTwoLists(ListNode list1, ListNode list2) {

  ListNode result = new ListNode();
  ListNode current = result;

  while(list1 != null && list2 != null){
    if(list1.val <= list2.val){
      current.next = list1;
      list1 = list1.next;
    }
    else{
      current.next = list2;
      list2 = list2.next;
    }
    current = current.next;
  }

  current.next = (list1 != null) ? list1 : list2;

  return result.next;
}
```
- **Approach 2:**
  - *Recursive approach*
- **⏳ Time Complexity:** `O(m+n)`
- **💾 Space Complexity:** `O(1)`

```java
// Code implementation for Problem 1
public ListNode mergeTwoLists(ListNode list1, ListNode list2) {

  if(list1 != null && list2 != null){

    if(list1.val <= list2.val){
      list1.next = mergeTwoLists(list1.next, list2);
      return list1;
    }
    else{
      list2.next = mergeTwoLists(list1, list2.next);
      return list2;
    }
  }

  if(list1 == null){
    return list2;
  }
  return list1;

}
```
---

