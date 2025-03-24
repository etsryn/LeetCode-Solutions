# 🔥 LeetCode Problem: Minimum Cost Walk in Weighted Graph

## 🎯 Problem Statement

There is an **undirected weighted graph** with `n` vertices labeled from `0` to `n - 1`.

You are given:
- An integer `n` representing the number of vertices.
- An array `edges`, where edges[i] = [$\text{u}_\text{i}$, vi, wi] indicates an edge between vertices `ui` and `vi` with weight `wi`.
- A 2D array `query`, where `query[i] = [si, ti]` represents a query to find the **minimum cost walk** from `si` to `ti`.

A **walk** on a graph is a sequence of vertices and edges. It starts and ends with a vertex, and each edge connects the vertex before it and the vertex after it. A walk can revisit the same edge or vertex multiple times.

The **cost** of a walk starting at node `u` and ending at node `v` is defined as the **bitwise AND** of all the edge weights in the walk:

$$
\text{cost} = w_0 \land w_1 \land w_2 \land \dots \land w_k
$$

Return an array `answer`, where `answer[i]` denotes the minimum cost of the walk for `query[i]`. If no such walk exists, return `-1`.

---

## 💡 Example Test Cases

### Example 1:
```plaintext
Input: n = 5, edges = [[0,1,7],[1,3,7],[1,2,1]], query = [[0,3],[3,4]]
Output: [1,-1]
```
**Explanation:**
- For the first query, we can take the path `0 -> 1 -> 2 -> 1 -> 3` with weights `7 & 1 & 1 & 7 = 1`.
- For the second query, there is no walk between nodes `3` and `4`, so the answer is `-1`.

### Example 2:
```plaintext
Input: n = 3, edges = [[0,2,7],[0,1,15],[1,2,6],[1,2,1]], query = [[1,2]]
Output: [0]
```
**Explanation:**
- For the query, the path `1 -> 2 -> 1 -> 2` with weights `1 & 6 & 1 = 0` achieves the minimum cost.

---

## 🔍 Constraints
- `2 <= n <= 10^5`
- `0 <= edges.length <= 10^5`
- `edges[i].length == 3`
- `0 <= ui, vi <= n - 1`, `ui != vi`
- `0 <= wi <= 10^5`
- `1 <= query.length <= 10^5`
- `query[i].length == 2`
- `0 <= si, ti <= n - 1`, `si != ti`

---

## 💡 Approach 1: Brute Force BFS (Time Complexity: $O(n^3)$)

### 🔧 C++ Solution
```cpp
#include <vector>
#include <queue>
#include <climits>
using namespace std;

class Solution {
public:
    vector<int> minCostWalk(int n, vector<vector<int>>& edges, vector<vector<int>>& queries) {
        vector<vector<pair<int, int>>> graph(n);
        for (auto& e : edges) {
            graph[e[0]].push_back({e[1], e[2]});
            graph[e[1]].push_back({e[0], e[2]});
        }

        vector<int> result;
        for (auto& q : queries) {
            int start = q[0], end = q[1];
            queue<pair<int, int>> q;
            q.push({start, INT_MAX});
            bool found = false;

            while (!q.empty()) {
                auto [node, cost] = q.front(); q.pop();
                if (node == end) {
                    result.push_back(cost);
                    found = true;
                    break;
                }
                for (auto& [neighbor, weight] : graph[node]) {
                    q.push({neighbor, cost & weight});
                }
            }
            if (!found) result.push_back(-1);
        }
        return result;
    }
};
```

#### Execution link:
```link
https://leetcode.com/problems/minimum-cost-walk-in-weighted-graph/submissions/XXXXX
```

---

## 💡 Approach 2: Optimized BFS with Bitwise Mask Pruning (Time Complexity: $O(n \times m)$)

### 🔧 C++ Solution
```cpp
#include <vector>
#include <queue>
#include <unordered_map>
using namespace std;

class Solution {
public:
    vector<int> minCostWalk(int n, vector<vector<int>>& edges, vector<vector<int>>& queries) {
        vector<unordered_map<int, int>> graph(n);
        for (auto& e : edges) {
            int u = e[0], v = e[1], w = e[2];
            graph[u][v] = graph[v][u] = (graph[u][v] ? graph[u][v] & w : w);
        }

        vector<int> res;
        for (auto& q : queries) {
            int start = q[0], end = q[1];
            if (start == end) {
                res.push_back(INT_MAX);
                continue;
            }

            queue<pair<int, int>> q;
            q.push({start, INT_MAX});
            unordered_map<int, int> visited;
            visited[start] = INT_MAX;
            bool found = false;

            while (!q.empty()) {
                auto [node, cost] = q.front(); q.pop();
                if (node == end) {
                    res.push_back(cost);
                    found = true;
                    break;
                }
                for (auto& [neighbor, weight] : graph[node]) {
                    int new_cost = cost & weight;
                    if (!visited.count(neighbor) || visited[neighbor] < new_cost) {
                        visited[neighbor] = new_cost;
                        q.push({neighbor, new_cost});
                    }
                }
            }
            if (!found) res.push_back(-1);
        }
        return res;
    }
};
```

#### Execution link:
```link
https://leetcode.com/problems/minimum-cost-walk-in-weighted-graph/submissions/XXXXX
```

---

## 🔍 Complexity Analysis

| Approach                        | Time Complexity | Space Complexity | Notes                       |
|---------------------------------|-----------------|------------------|----------------------------|
| Brute Force BFS                 | $O(n^3)$        | $O(n^2)$         | Inefficient for large graphs |
| Optimized BFS with Bitwise Mask | $O(n \times m)$ | $O(n + m)$       | Handles large graphs efficiently |

---

## 🎯 Key Takeaways

- **Brute Force BFS:** Tries all paths but slow for large graphs. 🚫  
- **Optimized BFS:** Uses bitwise mask pruning to minimize unnecessary paths. 🚀  
- **Memory Efficient:** Only tracks the best cost per node. 📌  

Write code that not only solves problems but stands the test of time — precision, performance, and clarity matter most. 🎯
