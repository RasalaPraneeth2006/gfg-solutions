## 01. C++ Solution || Easy Approach and Step by Step Explanation

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/path-exists/1?_gl=1*1e8zpps*_up*MQ..*_gs*MQ..&gclid=Cj0KCQjwlYHBBhD9ARIsALRu09pbgqNAyqVxhcm8IAnjUTMlLJhIC1w5aC7xa3QAQYivF9iTVK4woaUaAsehEALw_wcB&gbraid=0AAAAAC9yBkCuY1XCOe54dwAzS3bpeogBG)

### Problem Description

**Task:** Given an undirected graph with V vertices numbered from 0 to V - 1, represented by an adjacency list adj[][], where adj[i] contains all vertices adjacent to vertex i. Also given two vertices u and v, check whether a path exists between them.Return true if a path exists, otherwise return false.Examples: Input: adj[][] = [[2, 3], [2], [0, 1], [0], [5], [4]], u = 1, v = 5Output: falseExplanation: There is no path from vertex 1 to vertex 5.Input: adj[][] = [[2, 3], [2], [0, 1], [0], [5], [4]], u = 2, v = 3

#### Examples

##### Example 1

- **Output:**
```text
true
```
- **Explanation:** We can reach vertex 3 from vertex 2 via vertex 0.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(V + E)
- **Expected Auxiliary Space Complexity:** O(V + E)

### Accepted Solutions (1)

#### Solution 1 (C++)

- **Submitted:** 2026-11-28 21:25:36
- **Status:** Correct
- **Marks:** 2

```cpp
class Solution {
  public:
    bool checkPath(vector<vector<int>> &adj, int u, int v) {
        int n = adj.size();
        vector<bool> vis(n, false);
        queue<int> q;
        q.push(u);
        vis[u] = true;
        while (!q.empty()) {
            int curr = q.front();
            q.pop();
            if (curr == v) return true;
            for (int nei : adj[curr]) {
                if (!vis[nei]) {
                    vis[nei] = true;
                    q.push(nei);
                }
            }
        }
        return false;
    }
};
```

*Generated on: 11/28/2026, 9:26:21 PM*