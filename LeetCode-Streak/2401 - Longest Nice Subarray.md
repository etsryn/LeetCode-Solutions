# 🧠 LeetCode Problem: Longest Nice Subarray

## 📌 Problem Statement

You are given an **array** `nums` consisting of **positive integers**.

We call a **subarray** of `nums` **nice** if the **bitwise AND** of every **pair of elements** that are in **different positions** in the subarray is **equal to 0**.

Return the **length** of the **longest nice subarray**.

A **subarray** is a **contiguous part** of an array.

**Note:** Subarrays of **length 1** are always considered **nice**.

### Example 1:

```plaintext
Input: nums = [1,3,8,48,10]
Output: 3
Explanation: The longest nice subarray is [3,8,48]. This subarray satisfies the conditions:
- 3 AND 8 = 0.
- 3 AND 48 = 0.
- 8 AND 48 = 0.
It can be proven that no longer nice subarray can be obtained, so we return 3.
```

### Example 2:

```plaintext
Input: nums = [3,1,5,11,13]
Output: 1
Explanation: The length of the longest nice subarray is 1. Any subarray of length 1 can be chosen.
```

### Constraints:
- `1 <= nums.length <= 10^5`
- `1 <= nums[i] <= 10^9`

---

## 💡 Approach 1: Brute Force (Time Complexity: `O(n²)`)

### 🔧 C++ Solution
```cpp
class Solution {
    public:
    int longestNiceSubarray(vector<int>& nums) {
        int maxLen = 1;
        
        for(int i = 0; i < nums.size(); i++) {
            int bitmask = 0;
            for(int j = i; j < nums.size(); j++) {
                if((bitmask & nums[j]) != 0) break;
                bitmask |= nums[j];
                maxLen = max(maxLen, j - i + 1);
            }
        }
        return maxLen;
    }
};
```

#### Execution of above code:
```link
    https://leetcode.com/problems/longest-nice-subarray/submissions/1583918075/?envType=problem-list-v2&envId=2uzxgkqe
```

### 🔧 Java Solution
```java
class Solution {
    public int longestNiceSubarray(int[] nums) {
        int maxLen = 1;

        for(int i = 0; i < nums.length; i++) {
            int bitmask = 0;
            for(int j = i; j < nums.length; j++) {
                if((bitmask & nums[j]) != 0) break;
                bitmask |= nums[j];
                maxLen = Math.max(maxLen, j - i + 1);
            }
        }
        return maxLen;
    }
}
```

#### Execution of above code:
```link
    https://leetcode.com/problems/longest-nice-subarray/submissions/1583918891/?envType=problem-list-v2&envId=2uzxgkqe
```

---

## 💡 Approach 2: Sliding Window Optimization (Time Complexity: `O(n)`)

### 🔧 C++ Solution
```cpp
class Solution {
    public:
    int longestNiceSubarray(vector<int>& nums) {
        int bitmask = 0, left = 0, maxLen = 0;
        
        for(int right = 0; right < nums.size(); right++) {
            while((bitmask & nums[right]) != 0) {
                bitmask ^= nums[left];
                left++;
            }
            bitmask |= nums[right];
            maxLen = max(maxLen, right - left + 1);
        }
        return maxLen;
    }
};
```

#### Execution of above code:
```link
    https://leetcode.com/problems/longest-nice-subarray/submissions/1583919815/?envType=problem-list-v2&envId=2uzxgkqe
```

### 🔧 Java Solution
```java
class Solution {
    public int longestNiceSubarray(int[] nums) {
        int bitmask = 0, left = 0, maxLen = 0;

        for(int right = 0; right < nums.length; right++) {
            while((bitmask & nums[right]) != 0) {
                bitmask ^= nums[left];
                left++;
            }
            bitmask |= nums[right];
            maxLen = Math.max(maxLen, right - left + 1);
        }
        return maxLen;
    }
}
```

#### Execution of above code:
```link
    https://leetcode.com/problems/longest-nice-subarray/submissions/1583920529/?envType=problem-list-v2&envId=2uzxgkqe
```

---

## 🔍 Complexity Analysis

| Approach                   | Time Complexity | Space Complexity | Notes |
|----------------------------|-----------------|------------------|-------|
| Brute Force                | $O(n^2)$        | $O(1)$           | Checks all pairs of elements, inefficient |
| Sliding Window Optimization| $O(n)$          | $O(1)$           | Efficient by maintaining a dynamic bitmask |

---

## 🏅 Key Takeaways  

- **Brute Force:** Tries all pairs, inefficient for large inputs. 🚫  
- **Sliding Window:** Tracks valid subarray with bitmask, optimally expands and shrinks window. 🚀  
- **Edge Cases:** Handles duplicates and single-element arrays gracefully. 🔍  
- **Memory Efficient:** Both approaches use constant space. 📌  

Write code that not only solves problems but stands the test of time — precision, performance, and clarity matter most. 🎯
