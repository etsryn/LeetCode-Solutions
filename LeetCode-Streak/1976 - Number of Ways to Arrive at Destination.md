# 🧠 LeetCode Problem: Number of Ways to Arrive at Destination

## 📌 Problem Statement
You are in a city that consists of `n` intersections numbered from `0` to `n - 1` with bi-directional roads between some intersections. The inputs are generated such that you can reach any intersection from any other intersection and that there is at most one road between any two intersections.

You are given an integer `n` and a 2D integer array `roads` where `roads[i] = [uᵢ, vᵢ, timeᵢ]` means that there is a road between intersections `uᵢ` and `vᵢ` that takes `timeᵢ` minutes to travel. You want to know **in how many ways you can travel from intersection `0` to intersection `n - 1` in the shortest amount of time**.

Return the number of ways you can arrive at your destination in the shortest amount of time. Since the answer may be large, return it modulo `10⁹ + 7`.

### Example 1:
![Example Diagram](../Attached%20Images/1976_Fig_1.jpg)
```plaintext
Input: n = 7, roads = [[0,6,7],[0,1,2],[1,2,3],[1,3,3],[6,3,3],[3,5,1],[6,5,1],[2,5,1],[0,4,5],[4,6,2]]
Output: 4
```

### Example 2:
```plaintext
Input: n = 2, roads = [[1,0,10]]
Output: 1
Explanation: There is only one way to go from intersection 0 to intersection 1, and it takes 10 minutes.
```

### Constraints
- `1 <= n <= 200`
- `n - 1 <= roads.length <= n * (n - 1) / 2`
- `roads[i].length == 3`
- `0 <= uᵢ, vᵢ <= n - 1`
- `1 <= timeᵢ <= 10⁹`
- `uᵢ != vᵢ`
- There is at most one road connecting any two intersections.
- You can reach any intersection from any other intersection.

---

## 💡 Approach: Dijkstra's Algorithm (Time Complexity: `O(E log V)`)  

### 🛠️ C++ Solution
```cpp
class Solution {
public:
    int countPaths(int n, vector<vector<int>>& roads) {
        const int MOD = 1e9 + 7;
        vector<vector<pair<int, int>>> graph(n);
        
        for(auto& road : roads) {
            graph[road[0]].push_back({road[1], road[2]});
            graph[road[1]].push_back({road[0], road[2]});
        }
        
        vector<long long> dist(n, LLONG_MAX), ways(n, 0);
        
        priority_queue<pair<long long, int>, vector<pair<long long, int>>, greater<>> pq;
        pq.push({0, 0});
        dist[0] = 0;
        ways[0] = 1;
        
        while(!pq.empty()) {
            auto [time, node] = pq.top(); pq.pop();
            if(time > dist[node]) continue;
            for(auto& [neighbor, t] : graph[node]) {
                long long newDist = time + t;
                if(newDist < dist[neighbor]) {
                    dist[neighbor] = newDist;
                    ways[neighbor] = ways[node];
                    pq.push({newDist, neighbor});
                } else if(newDist == dist[neighbor]) {
                    ways[neighbor] = (ways[neighbor] + ways[node]) % MOD;
                }
            }
        }
        return ways[n - 1];
    }
};
```

#### Execution of above code:
```link
    https://leetcode.com/problems/number-of-ways-to-arrive-at-destination/submissions/1589751591/?envType=problem-list-v2&envId=2uzxgkqe
```

### 🛠️ Java Solution
```java
import java.util.*;

class Solution {
    public int countPaths(int n, int[][] roads) {
        final int MOD = 1_000_000_007;
        
        List<List<int[]>> graph = new ArrayList<>();
        for(int i = 0; i < n; i++) graph.add(new ArrayList<>());
        for(int[] road : roads) {
            graph.get(road[0]).add(new int[]{road[1], road[2]});
            graph.get(road[1]).add(new int[]{road[0], road[2]});
        }

        long[] dist = new long[n];
        int[] ways = new int[n];
        
        Arrays.fill(dist, Long.MAX_VALUE);
        dist[0] = 0;
        ways[0] = 1;

        PriorityQueue<long[]> pq = new PriorityQueue<>(Comparator.comparingLong(a -> a[0]));
        pq.offer(new long[]{0, 0});

        while(!pq.isEmpty()) {
            long[] top = pq.poll();
            long d = top[0];
            int node = (int) top[1];

            if(d > dist[node]) continue;

            for(int[] neighbor : graph.get(node)) {
                int nextNode = neighbor[0];
                long newDist = d + neighbor[1];

                if(newDist < dist[nextNode]) {
                    dist[nextNode] = newDist;
                    ways[nextNode] = ways[node];
                    pq.offer(new long[]{newDist, nextNode});
                } else if(newDist == dist[nextNode]) {
                    ways[nextNode] = (ways[nextNode] + ways[node]) % MOD;
                }
            }
        }

        return ways[n - 1]; // Number of shortest paths to the last node
    }
}
```

#### Execution of above code:
```link
    https://leetcode.com/problems/number-of-ways-to-arrive-at-destination/submissions/1589753694/?envType=problem-list-v2&envId=2uzxgkqe
```

---

## 📊 Complexity Analysis

| Approach    | Time Complexity | Space Complexity | Notes |
|------------|----------------|----------------|--------|
| Dijkstra's Algorithm | `O(E log V)` | `O(V + E)` | Efficient for shortest path calculations |

### 🔑 Key Takeaways:
- Uses **Priority Queue (Min-Heap)** to efficiently find the shortest path.
- Maintains `ways[]` array to count different paths that yield the shortest time.
- **Time Complexity:** `O(E log V)`, efficient for large graphs.

Write code that not only solves problems but stands the test of time — precision, performance, and clarity matter most. 🎯
