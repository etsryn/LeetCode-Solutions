# 🧠 LeetCode Problem: Add Two Numbers

## 📌 Problem Statement

You are given two **non-empty** linked lists representing two non-negative integers. The digits are stored in **reverse order**, and each of their nodes contains a **single digit**. Add the two numbers and return the sum as a linked list.

You may assume the two numbers **do not** contain any leading zero, except the number 0 itself.

### Example 1:

```plaintext
Input: l1 = [2,4,3], l2 = [5,6,4]
Output: [7,0,8]
Explanation: 342 + 465 = 807.
```

### Example 2:

```plaintext
Input: l1 = [0], l2 = [0]
Output: [0]
```

### Example 3:

```plaintext
Input: l1 = [9,9,9,9,9,9,9], l2 = [9,9,9,9]
Output: [8,9,9,9,0,0,0,1]
```

### Constraints:

- The number of nodes in each linked list is in the range [1, 100].
- 0 <= Node.val <= 9
- It is guaranteed that the list represents a number that does not have leading zeros.

---

## 💡 Approach 1: Iterative (Time Complexity: O(max(n, m)))

### 🔧 C++ Solution
```cpp
struct ListNode {
    int val;
    ListNode *next;
    ListNode(int x) : val(x), next(nullptr) {}
};

ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
    ListNode* dummy = new ListNode(0);
    ListNode* current = dummy;
    int carry = 0;

    while (l1 != nullptr || l2 != nullptr || carry != 0) {
        int sum = (l1 ? l1->val : 0) + (l2 ? l2->val : 0) + carry;
        carry = sum / 10;
        current->next = new ListNode(sum % 10);
        current = current->next;
        if (l1) l1 = l1->next;
        if (l2) l2 = l2->next;
    }

    return dummy->next;
}
```

### 🔧 Java Solution
```java
class ListNode {
    int val;
    ListNode next;
    ListNode(int x) { val = x; }
}

public class AddTwoNumbers {
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        ListNode dummy = new ListNode(0);
        ListNode current = dummy;
        int carry = 0;

        while (l1 != null || l2 != null || carry != 0) {
            int sum = (l1 != null ? l1.val : 0) + (l2 != null ? l2.val : 0) + carry;
            carry = sum / 10;
            current.next = new ListNode(sum % 10);
            current = current.next;
            if (l1 != null) l1 = l1.next;
            if (l2 != null) l2 = l2.next;
        }

        return dummy.next;
    }
}
```

---

## 💡 Approach 2: Recursive (Time Complexity: O(max(n, m)))

### 🔧 C++ Solution
```cpp
ListNode* addTwoNumbersRecursive(ListNode* l1, ListNode* l2, int carry = 0) {
    if (!l1 && !l2 && carry == 0) return nullptr;
    int sum = (l1 ? l1->val : 0) + (l2 ? l2->val : 0) + carry;
    ListNode* node = new ListNode(sum % 10);
    node->next = addTwoNumbersRecursive(l1 ? l1->next : nullptr, l2 ? l2->next : nullptr, sum / 10);
    return node;
}
```

### 🔧 Java Solution
```java
public ListNode addTwoNumbersRecursive(ListNode l1, ListNode l2, int carry) {
    if (l1 == null && l2 == null && carry == 0) return null;
    int sum = (l1 != null ? l1.val : 0) + (l2 != null ? l2.val : 0) + carry;
    ListNode node = new ListNode(sum % 10);
    node.next = addTwoNumbersRecursive(l1 != null ? l1.next : null, l2 != null ? l2.next : null, sum / 10);
    return node;
}
```

---

## 🔍 Complexity Analysis

| Approach    | Time Complexity | Space Complexity |
|-------------|------------------|------------------|
| Iterative   | O(max(n, m))     | O(max(n, m))     |
| Recursive   | O(max(n, m))     | O(max(n, m))     |

---

## 🏅 Key Takeaways

- **Iterative:** Clean and straightforward, easy to understand.
- **Recursive:** More compact, but recursion depth may cause stack overflow on very large inputs.
- **Edge Cases:** Handles different length lists, carryovers, and single-node edge cases.

Happy problem solving! 🚀


