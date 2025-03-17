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

- The number of nodes in each linked list is in the range `[1, 100]`.
- `0 <= Node.val <= 9`
- It is guaranteed that the list represents a number that does not have leading zeros.

---

## 💡 Approach: Iterative (Time Complexity: `O(max(n, m))`)

### 🔧 C++ Solution
```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution {
public:
    ListNode* addTwoNumbers(ListNode *l1, ListNode *l2) {
        ListNode *dummy = new ListNode(0);
        ListNode *current = dummy;
        int carry = 0;

        while(l1 != nullptr || l2 != nullptr || carry != 0) {
            int sum = (l1 ? l1->val : 0) + (l2 ? l2->val : 0) + carry;
            carry = sum / 10;
            current->next = new ListNode(sum % 10);
            current = current->next;
            if(l1) l1 = l1->next;
            if(l2) l2 = l2->next;
        }

        return dummy->next;
    }
};
```

#### Execution of above code:
```link
    https://leetcode.com/problems/add-two-numbers/submissions/1573106853/
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

#### Execution of above code:
```link
    https://leetcode.com/problems/add-two-numbers/submissions/1573098987/
```

---


## 🔍 Complexity Analysis

| Approach    | Time Complexity | Space Complexity |
|-------------|------------------|------------------|
| Iterative   | $O(max(n, m))$     | $O(max(n, m))$     |

---

## 🏅 Key Takeaways  

- **Iterative & Efficient:** Uses a **dummy node** and **single-pass iteration** to construct the sum list efficiently.  
- **Handles Unequal Lengths:** Works even if `l1` and `l2` have different lengths, filling missing values as `0`.  
- **Manages Carry Properly:** Correctly handles carry propagation across nodes, even when it extends beyond the last digits.  
- **Memory Efficient:** Uses **O(max(n, m))** space, as required for storing the result list.  
- **Edge Case Handling:** Works for inputs like `[0] + [0]`, very large numbers, and cases where carry extends the list.  
- **Clear & Modular:** Uses a `dummy` node for simplicity and avoids unnecessary condition checks.

Write code that not only solves problems but stands the test of time — precision, performance, and clarity matter most. 🎯
