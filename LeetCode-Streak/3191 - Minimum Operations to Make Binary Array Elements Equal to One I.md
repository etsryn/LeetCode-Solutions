# 🧠 LeetCode Problem: Minimum Operations to Make Binary Array Elements Equal to One I

## 📌 Problem Statement

You are given a **binary array** `nums`.

You can do the following operation on the array **any** number of times (possibly zero):

- Choose **any** 3 **consecutive** elements from the array and **flip all** of them.  
(**Flipping** an element means changing its value from `0` to `1`, and from `1` to `0`.)

Return the **minimum** number of operations required to make all elements in `nums` equal to 1. If it is impossible, return -1.

### Example 1:

```plaintext
Input: nums = [0,1,1,1,0,0]
Output: 3
Explanation:
We can do the following operations:
- Choose the elements at indices 0, 1, and 2. The resulting array is `nums = [1,0,0,1,0,0]`.
- Choose the elements at indices 1, 2, and 3. The resulting array is `nums = [1,1,1,0,0,0]`.
- Choose the elements at indices 3, 4, and 5. The resulting array is `nums = [1,1,1,1,1,1]`.
```

### Example 2:

```plaintext
Input: nums = [0,1,1,1]
Output: -1
Explanation:
It is impossible to make all elements equal to 1.
```

### Constraints:
- `3 <= nums.length <= 10^5`
- `0 <= nums[i] <= 1`

---

## 💡 Approach 1: Brute Force (Time Complexity: $O(n^3)$)

### 🔧 C++ Solution
```cpp
class Solution {
    public:
    int minOperations(vector<int>& nums) {
       int n = nums.size();
        int ops = 0;
        
        for(int i = 0; i <= n - 3; i++) {
            if(nums[i] == 0) {
                ops++;
                nums[i] ^= 1;
                nums[i+1] ^= 1;
                nums[i+2] ^= 1;
            }
        }
        
        for(int i = 0; i < n; i++) {
            if(nums[i] == 0) return -1;
        }
        return ops; 
    }
};
```

#### Execution of above code:
```link
    https://leetcode.com/problems/minimum-operations-to-make-binary-array-elements-equal-to-one-i/submissions/1579388290/?envType=daily-question&envId=2025-03-19
```

### 🔧 Java Solution
```java
class Solution {
    public int minOperations(int[] nums) {
        int n = nums.length;
        int ops = 0;
        
        for(int i = 0; i <= n-3; i++) {
            if(nums[i] == 0) {
                ops++;
                nums[i] ^= 1;
                nums[i+1] ^= 1;
                nums[i+2] ^= 1;
            }
        }
        
        for(int num : nums) {
            if(num == 0) return -1;
        }
        return ops;
    }
}
```

#### Execution of above code:
```link
    https://leetcode.com/problems/minimum-operations-to-make-binary-array-elements-equal-to-one-i/submissions/1579389814/?envType=daily-question&envId=2025-03-19
```

---

## 💡 Approach 2: Greedy Sliding Window (Time Complexity: $O(n)$)

### 🔧 C++ Solution
```cpp
class Solution {
    public:
    int minOperations(vector<int>& nums) {
        int n = nums.size();
        int ops = 0;
        
        for(int i = 0; i < n-2; i++) {
            if(nums[i] == 0) {
                ops++;
                nums[i] ^= 1;
                nums[i+1] ^= 1;
                nums[i+2] ^= 1;
            }
        }
        return (nums[n-1] == 0 || nums[n-2] == 0) ? -1 : ops;
    }
};
```

### Execution of above code:
```link
    https://leetcode.com/problems/minimum-operations-to-make-binary-array-elements-equal-to-one-i/submissions/1579391190/?envType=daily-question&envId=2025-03-19
```

### 🔧 Java Solution
```java
class Solution {
    public int minOperations(int[] nums) {
        int n = nums.length;
        int ops = 0;
        
        for(int i = 0; i < n-2; i++) {
            if(nums[i] == 0) {
                ops++;
                nums[i] ^= 1;
                nums[i+1] ^= 1;
                nums[i+2] ^= 1;
            }
        }
        return (nums[n-1] == 0 || nums[n-2] == 0) ? -1 : ops;
    }
}
```

### Execution of above code:
```link
    https://leetcode.com/problems/minimum-operations-to-make-binary-array-elements-equal-to-one-i/submissions/1579393577/?envType=daily-question&envId=2025-03-19
```

---

## 🔍 Complexity Analysis

| Approach              | Time Complexity | Space Complexity | Notes |
|-----------------------|-----------------|------------------|-------|
| Brute Force           | $O(n^3)$        | $O(1)$           | Tries all possible flips — very inefficient. 🚫 |
| Greedy Sliding Window | $O(n)$          | $O(1)$           | Flips only when necessary — highly optimized. 🚀 |

---

## 🏅 Key Takeaways  

- **Brute Force:** Tries all possible flips, highly inefficient. 🚫  
- **Greedy Sliding Window:** Efficiently flips consecutive segments, minimizing operations. 🚀  
- **Edge Cases:** Handles arrays with trailing 0s and checks infeasible configurations properly. 🔍  
- **Memory Efficient:** Both approaches use constant space. 📌  

Write code that not only solves problems but stands the test of time — precision, performance, and clarity matter most. 🎯
