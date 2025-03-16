# 🧠 LeetCode Problem: 2594 - Minimum Time to Repair Cars

## 📌 Problem Statement

You are given an integer array `ranks` representing the ranks of some mechanics. ranks<sub>i</sub> is the rank of the i<sup>th</sup> mechanic. A mechanic with a rank `r` can repair n cars in `r * n`<sup>`2`</sup> minutes.

You are also given an integer `cars` representing the total number of cars waiting in the garage to be repaired.

Return *the* ***minimum*** *time taken to repair all the cars*.

**Note:** All the mechanics can repair the cars simultaneously.

### Example 1:
```plaintext
Input: ranks = [4,2,3,1], cars = 10
Output: 16
Explanation: 
- The first mechanic will repair two cars. The time required is 4 * 2 * 2 = 16 minutes.
- The second mechanic will repair two cars. The time required is 2 * 2 * 2 = 8 minutes.
- The third mechanic will repair two cars. The time required is 3 * 2 * 2 = 12 minutes.
- The fourth mechanic will repair four cars. The time required is 1 * 4 * 4 = 16 minutes.
```

### Example 2:
```plaintext
Input: ranks = [5,1,8], cars = 6
Output: 16
Explanation: 
- The first mechanic will repair one car. The time required is 5 * 1 * 1 = 5 minutes.
- The second mechanic will repair four cars. The time required is 1 * 4 * 4 = 16 minutes.
- The third mechanic will repair one car. The time required is 8 * 1 * 1 = 8 minutes.
```

### Constraints:

- `1 <= ranks.length <= 10^5`
- `1 <= ranks[i] <= 100`
- `1 <= cars <= 10^6`

---

## 💡 Approach: Binary Search (Optimal — Balanced Mechanics) (Time Complexity: O(n * log(10<sup>14</sup>))

### 🔧 C++ Solution

```cpp
class Solution {
    public:
    long long repairCars(vector<int> &ranks, int cars) {
        long long left=1, right=1e14, result=right;
        while(left<=right) {
            long long mid = (left+right)/2;
            if(canRepair(ranks, cars, mid)) {
                result = mid;
                right = mid - 1;
            } else {
                left = mid + 1;
            }
        }
        return result;
    }
    
    bool canRepair(vector<int> &ranks, int cars, long long time) {
        int repaired = 0;
        for(int rank : ranks) {
            repaired += sqrt(time/rank);
            if(repaired >= cars) return true;
        }
        return false;
    }
};
```

#### Execution of above code:
```link
    https://leetcode.com/problems/minimum-time-to-repair-cars/submissions/1575530670/?envType=daily-question&envId=2025-03-16
```

### 🔧 Java Solution

```java
class Solution {
    public static long repairCars(int[] ranks, int cars) {
        long left = 1, right = (long) 1e14, result = right;
        while(left <= right) {
            final long mid = (left + right) / 2;
            if(canRepair(ranks, cars, mid)) {
                result = mid;
                right = mid - 1;
            } else {
                left = mid + 1;
            }
        }
        return result;
    }
    private static boolean canRepair(int[] ranks, int cars, long time) {
        int repaired = 0;
        for(int rank : ranks) {
            repaired += Math.sqrt(time/rank);
            if(repaired >= cars) return true;
        }
        return false;
    }
}
```

#### Execution of above code:
```link
    https://leetcode.com/problems/minimum-time-to-repair-cars/submissions/1575529366/?envType=daily-question&envId=2025-03-16
```

✅ **Time Complexity:** $O(n \times \log(10^{14}))$

✅ **Space Complexity:** O(1)

---

## 🔍 Comprehensive Complexity Analysis

| Approach          | Time Complexity    | Space Complexity | Notes                                       |
| ----------------- | ------------------ | ---------------- | ------------------------------------------- |
| Binary Search     | $O(n \times \log(10^{14}))$   | O(1)             | Optimal — Balanced distribution      |

---

## 🏅 Key Takeaways

- **Understand first, optimize later.**
- **Binary Search on Time** is the golden approach here.
- **Edge cases:** Handles small/large cars and mechanics efficiently.

Write code that not only solves problems but stands the test of time — precision, performance, and clarity matter most. 🎯
