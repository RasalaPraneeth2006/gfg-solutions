## 01. Count Tree Paths With Limited Max Edge Weight

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/possible-paths--141628/1)

### Problem Description

**Task:** Given a weighted tree with n nodes, numbered from 1 to n and n - 1 edges, where each edge is represented as [u, v, w] indicating an edge between nodes u and v with weight w.You are also given an array queries[], where each queries[i] represents a maximum allowed edge weight.For each query x, find the number of distinct paths in the tree such that the maximum edge weight along the path is less than or equal to x.Return an array containing the number of valid paths for each query.Note: A path from node u to node v and the path from node v to node u are considered the same path. A path must contain at least one edge. A path from a node to itself is not considered.Examples:Input: n = 3, edges[][] = [[1, 2, 1], [2, 3, 4]], queries[] = [3]

#### Examples

##### Example 1

- **Output:**
```text
[1, 3, 4]
```
- **Explanation:** For x = 1, only the edge [2, 3, 1] satisfies the condition. Therefore, the only valid path is 2 - > 3, giving an answer of 1. For x = 3, the edges [2, 3, 1] and [1, 2, 3] can be used. They form three valid paths: 1 - > 2, 2 - > 3, and 1 - > 3. For x = 5, the edges with weights 1, 3, and 4 can be used. They form four valid paths: 1 - > 2, 2 - > 3, 1 - > 3, and 5 - > 7.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(nlogn + qlogn)
- **Expected Auxiliary Space Complexity:** O(n)

### Accepted Solutions (1)

#### Solution 1 (C++)

- **Submitted:** 2026-11-03 00:03:46
- **Status:** Correct
- **Marks:** 8

```cpp
class Solution {
    long long ans;

    int Find(int i, vector<int>& parent) {
        if (parent[i] == i)
            return i;
        return parent[i] = Find(parent[i], parent);
    }

    long long Union(int a, int b, vector<int>& parent, vector<int>& sz) {
        int ra = Find(a, parent);
        int rb = Find(b, parent);
        if (ra != rb) {
            if (sz[ra] < sz[rb])
                swap(ra, rb);
            ans += (long long)sz[ra] * sz[rb];
            parent[rb] = ra;
            sz[ra] += sz[rb];
        }
        return ans;
    }

public:
    vector<int> maximumWeight(int n, vector<vector<int>>& edges, vector<int>& queries) {
        ans = 0;
        vector<int> parent(n + 1, 0), sz(n + 1, 0);
        for (int i = 0; i <= n; i++) {
            parent[i] = i;
            sz[i] = 1;
        }

        vector<pair<int, pair<int, int>>> wt;
        for (int i = 0; i < edges.size(); i++) {
            wt.push_back({edges[i][2], {edges[i][0], edges[i][1]}});
        }
        sort(wt.begin(), wt.end());

        map<int, int> mp;
        for (int i = 0; i < n - 1; i++) {
            int val = wt[i].first;
            int firstnode = wt[i].second.first;
            int secondnode = wt[i].second.second;
            mp[val] = Union(firstnode, secondnode, parent, sz);
        }

        vector<int> res;
        for (int i = 0; i < queries.size(); i++) {
            auto val = mp.upper_bound(queries[i]);
            if (val == mp.begin()) {
                res.push_back(0);
            } else {
                val--;
                res.push_back(val->second);
            }
        }
        return res;
    }
};
```

*Generated on: 11/3/2026, 12:05:11 AM*