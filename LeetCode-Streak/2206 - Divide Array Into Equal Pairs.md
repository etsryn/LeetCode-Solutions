# 🔥 LeetCode Problem: Divide Array Into Equal Pairs

## 📌 Problem Statement

You are given an integer array `nums` consisting of `2 * n` integers.

You need to divide `nums` into `n` pairs such that:

- Each element belongs to exactly one pair.
- The elements present in a pair are equal.

Return `true` if `nums` can be divided into `n` pairs, otherwise return `false`.

### Example 1:

```plaintext
Input: nums = [3,2,3,2,2,2]
Output: true
Explanation: 
There are 6 elements in nums, so they should be divided into 6 / 2 = 3 pairs.
If nums is divided into the pairs (2, 2), (3, 3), and (2, 2), it will satisfy all the conditions.
```

### Example 2:

```plaintext
Input: nums = [1,2,3,4]
Output: false
Explanation: 
There is no way to divide nums into 4 / 2 = 2 pairs such that the pairs satisfy every condition.
```

### Constraints:

- `nums.length == 2 * n`
- `1 <= n <= 500`
- `1 <= nums[i] <= 500`

---

## 💡 Approach 1: Brute Force (Inefficient) (Time Complexity: `O(n log n)`)

### 🔧 C++ Solution

```cpp
class Solution {
    public:
    bool divideArray(vector<int> &nums) {
        sort(nums.begin(), nums.end());
        for(int i = 0; i < nums.size(); i += 2) {
            if(nums[i] != nums[i+1]) return false;
        }
        return true;
    }
};
```

#### Execution of above code:
```link
    https://leetcode.com/problems/divide-array-into-equal-pairs/submissions/1576954906/?envType=daily-question&envId=2025-03-17
```

### 🔧 Java Solution

```java
class Solution {
    public boolean divideArray(int[] nums) {
        Arrays.sort(nums);
        for(int i = 0; i < nums.length; i += 2) {
            if(nums[i] != nums[i + 1]) return false;
        }
        return true;
    }
}
```

#### Execution of above code:
```link
    https://leetcode.com/problems/divide-array-into-equal-pairs/submissions/1576956076/?envType=daily-question&envId=2025-03-17
```

✅ **Time Complexity:** $O(n\ \log n)$

✅ **Space Complexity:** $O(1)$

---

## 💡 Approach 2: Frequency Count (Optimized Solution) (Time Complexity: `O(n)`)

### 🔧 C++ Solution

```cpp
class Solution {
    public:
    bool divideArray(vector<int> &nums) {
        unordered_map<int, int> freq;
    
        for(int num : nums) {
            freq[num]++;
        }

        for(auto& [num, count] : freq) {
            if(count % 2 != 0) return false;
        }
        return true;
    }
};
```

#### Execution of above code:
```link
    https://leetcode.com/problems/divide-array-into-equal-pairs/submissions/1576958736/?envType=daily-question&envId=2025-03-17
```

### 🔧 Java Solution

```java
class Solution {
    public boolean divideArray(int[] nums) {
        HashMap<Integer, Integer> freq = new HashMap<>();
        for(int num : nums) {
            freq.put(num, freq.getOrDefault(num, 0) + 1);
        }
        for(int count : freq.values()) {
            if(count % 2 != 0) return false;
        }
        return true;
    }
}
```

#### Execution of above code:
```link
    https://leetcode.com/problems/divide-array-into-equal-pairs/submissions/1576959999/?envType=daily-question&envId=2025-03-17
```

✅ **Time Complexity:** $O(n)$

✅ **Space Complexity:** $O(n)$

---

## 💡 Approach 3: Bit Manipulation (Highly Optimized) (Time Complexity: `O(n)`)

### 🔧 C++ Solution

```cpp
class Solution {
    public:
    bool divideArray(vector<int> &nums) {
        vector<int> count(501, 0);
        for(int num : nums) {
            count[num]++;
        }
        for(int i = 0; i <= 500; ++i) {
            if(count[i] % 2 != 0) return false;
        }
        return true;
    }
};
```

#### Execution of above code:
```link
    https://leetcode.com/problems/divide-array-into-equal-pairs/submissions/1576960869/?envType=daily-question&envId=2025-03-17
```

### 🔧 Java Solution

```java
class Solution {
    public boolean divideArray(int[] nums) {
        int[] count = new int[501];
        for (int num : nums) count[num]++;
        for (int c : count) if (c % 2 != 0) return false;
        return true;
    }
}
```

#### Execution of above code:
```link
    https://leetcode.com/problems/divide-array-into-equal-pairs/submissions/1576961902/?envType=daily-question&envId=2025-03-17
```

✅ **Time Complexity:** $O(n)$

✅ **Space Complexity:** O(500) → **$O(1)$**

---

## 🔍 Complexity Analysis

| Approach              | Time Complexity | Space Complexity | Notes                              |
| --------------------- | ---------------- | ---------------- | ---------------------------------- |
| Brute Force           | $O(n\ \log n)$       | $O(1)$             | Sort-based comparison per element  |
| Frequency Count       | $O(n)$             | $O(n)$             | Faster — Uses counts only        |
| Bit Manipulation      | $O(n)$             | $O(1)$             | Most optimized — Constant space  |

---

## 🏅 Key Takeaways

- **Multiple approaches** — from brute force to optimized.
- **Handles large inputs efficiently** — optimal solutions run in linear time.
- **Space optimization** — bit manipulation approach reduces space to constant.
- **Edge case handling** — covers scenarios with duplicates, unique numbers, and small/large arrays.

Write code that not only solves problems but stands the test of time — precision, performance, and clarity matter most. 🎯
