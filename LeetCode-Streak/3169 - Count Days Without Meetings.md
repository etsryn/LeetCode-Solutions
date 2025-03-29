# 🧠 LeetCode Problem: Count Days Without Meetings

## 📌 Problem Statement

You are given a positive integer `days` representing the total number of days an employee is available for work (starting from day `1`). You are also given a `2D` array `meetings` of size `n` where, `meetings[i] = [start_i, end_i]` represents the starting and ending days of meeting `i` (inclusive).

Return the count of days when the employee is available for work but **no meetings** are scheduled.

Note: The meetings may overlap.

### Example 1:
```plaintext
Input: days = 10, meetings = [[5,7],[1,3],[9,10]]
Output: 2
Explanation: There is no meeting scheduled on the 4ᵗʰ and 8ᵗʰ days.
```
### Example 2:
```plaintext
Input: days = 5, meetings = [[2,4],[1,3]]
Output: 1
Explanation: There is no meeting scheduled on the 5ᵗʰ day.
```
### Example 3:
```plaintext
Input: days = 6, meetings = [[1,6]]
Output: 0
Explanation: Meetings are scheduled for all working days.
```
### Constraints
- `1 <= days <= 10⁹`<br />
- `1 <= meetings.length <= 10⁵`<br />
- `meetings[i].length == 2`<br />
- `1 <= meetings[i][0] <= meetings[i][1] <= days`<br />

---

## 💡 Approach 1: Brute Force (Time Complexity: `O(n*d)`, Space Complexity: `O(1)`) ❌ (Inefficient for large `days`)

### 🔧 C++ Solution [Code will not work, it will give Time Limit Exceeded Issue]
```cpp
class Solution {
public:
    int countDays(int days, vector<vector<int>>& meetings) {
        unordered_set<int> meetingDays;
        for(auto& m : meetings) {
            for(int d = m[0]; d <= m[1]; d++) {
                meetingDays.insert(d);
            }
        }
        return days - meetingDays.size();
    }
};
```

### 🔧 Java Solution [Code will not work, it will give Time Limit Exceeded Issue]
```java
import java.util.*;
class Solution {
    public int countDays(int days, int[][] meetings) {
        Set<Integer> meetingDays = new HashSet<>();
        for(int[] m : meetings) {
            for(int d = m[0]; d <= m[1]; d++) {
                meetingDays.add(d);
            }
        }
        return days - meetingDays.size();
    }
}
```

---

## 💡 Approach 2: Sorting & Merging Intervals (Time Complexity: `O(n log n)`, Space Complexity: `O(n)`) ✅

### 🔧 C++ Solution
```cpp
class Solution {
public:
    int countDays(int days, vector<vector<int>>& meetings) {
        sort(meetings.begin(), meetings.end());
        int covered = 0, lastEnd = 0;
        
        for(auto& m : meetings) {
            if(m[1] <= lastEnd) continue;
            
            if(m[0] > lastEnd + 1) {
                covered += (m[1] - m[0] + 1);
            } else {
                covered += (m[1] - lastEnd);
            }
            lastEnd = max(lastEnd, m[1]);
        }        
        return days - covered;
    }
};
```

### Execution of above code:
```link
  https://leetcode.com/problems/count-days-without-meetings/submissions/1589813433/?envType=problem-list-v2&envId=2uzxgkqe
```

### 🔧 Java Solution
```java
class Solution {
    public int countDays(int days, int[][] meetings) {
        Arrays.sort(meetings, (a, b) -> Integer.compare(a[0], b[0]));
        int covered = 0, lastEnd = 0;
        for (int[] m : meetings) {
            if (m[1] <= lastEnd) continue;
            if (m[0] > lastEnd + 1) covered += (m[1] - m[0] + 1);
            else covered += (m[1] - lastEnd);
            lastEnd = Math.max(lastEnd, m[1]);
        }
        return days - covered;
    }
}
```

### Execution of above code:
```link
  https://leetcode.com/problems/count-days-without-meetings/submissions/1589814417/?envType=problem-list-v2&envId=2uzxgkqe
```

---

## 💡 Approach 3: Sweep Line Algorithm (Optimal Solution, `O(n log n)`, Space Complexity: `O(n)`) ✅✅

### 🔧 C++ Solution
```cpp
class Solution {
public:
    int countDays(int days, vector<vector<int>>& meetings) {
        vector<pair<int, int>> events;
        for(auto& m : meetings) {
            events.push_back({m[0], 1});
            events.push_back({m[1] + 1, -1});
        }
        sort(events.begin(), events.end());
        int freeDays = 0, ongoingMeetings = 0, lastDay = 1;
        for(auto& e : events) {
            if(ongoingMeetings == 0) {
                freeDays += e.first - lastDay;
            }
            ongoingMeetings += e.second;
            lastDay = e.first;
        }
        return freeDays + (days - lastDay + 1);
    }
};
```

### Execution of above code:
```link
  https://leetcode.com/problems/count-days-without-meetings/submissions/1589814826/?envType=problem-list-v2&envId=2uzxgkqe
```

### 🔧 Java Solution
```java
class Solution {
    public int countDays(int days, int[][] meetings) {
        List<int[]> events = new ArrayList<>();
        for(int[] m : meetings) {
            events.add(new int[]{m[0], 1});
            events.add(new int[]{m[1] + 1, -1});
        }
        events.sort((a, b) -> Integer.compare(a[0], b[0]));
        int freeDays = 0, ongoingMeetings = 0, lastDay = 1;
        for(int[] e : events) {
            if(ongoingMeetings == 0) {
                freeDays += e[0] - lastDay;
            }
            ongoingMeetings += e[1];
            lastDay = e[0];
        }
        return freeDays + (days - lastDay + 1);
    }
}
```

### Execution of above code:
```link
  https://leetcode.com/problems/count-days-without-meetings/submissions/1589815332/?envType=problem-list-v2&envId=2uzxgkqe
```

---

## 🔍 Complexity Analysis

| Approach                 | Time Complexity | Space Complexity | Notes                                                        |
|--------------------------|-----------------|------------------|--------------------------------------------------------------|
| **Brute Force**          | `O(n*d)`        | `O(1)`           | Code will not work, it will give Time Limit Exceeded Issue   |
| **Sorting & Merging**    | `O(n log n)`    | `O(n)`           | Sorts and merges intervals to find available days            |
| **Sweep Line Algorithm** | `O(n log n)`    | `O(n)`           | Uses event points to track meetings and count free days      |

---

## 🏅 Key Takeaways  
- **Brute Force:** Too slow for large inputs (`days` up to `10^9`). ❌ [Code will not work, it will give Time Limit Exceeded Issue]
- **Sorting & Merging:** Efficient, but needs sorting. ✅
- **Sweep Line Algorithm:** Best approach with **O(n log n)** complexity. ✅✅
- **Handles Overlapping Meetings:** Ensures correct free day calculation.
- **Real-World Usage:** Useful for scheduling problems, time-slot management, and booking systems.

**Choose the right approach based on input constraints! ✨**
