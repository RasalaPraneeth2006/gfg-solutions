## 01. Two Pairs with Same Sum

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/satisfy-the-equation5847/1?_gl=1*1hb3dl*_up*MQ..*_gs*MQ..&gclid=Cj0KCQjwlYHBBhD9ARIsALRu09pbgqNAyqVxhcm8IAnjUTMlLJhIC1w5aC7xa3QAQYivF9iTVK4woaUaAsehEALw_wcB&gbraid=0AAAAAC9yBkCuY1XCOe54dwAzS3bpeogBG)

### Problem Description

**Task:** Given an array arr[] of positive integers, find four indices a, b, c, and d such that arr[a] + arr[b] = arr[c] + arr[d], where a, b, c, d are all distinct indices.If multiple such quadruplets exist, return the one that is lexicographically smallest when the indices are considered in the order a, b, c, d. If no such quadruplet exists, return {-1, -1, -1, -1}. Ensure a < b and c < d, and the pair (a, b) is lexicographically smaller than the pair (c, d).Examples:Input: arr[] = [3, 4, 7, 1, 2, 9, 8]

#### Examples

##### Example 1

- **Output:**
```text
[-1, -1, -1, -1]
```
- **Explanation:** No two distinct pairs of indices produce the same sum.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n^2)
- **Expected Auxiliary Space Complexity:** O(n^2)

### Accepted Solutions (1)

#### Solution 1 (C++)

- **Submitted:** 2026-11-24 23:55:23
- **Status:** Correct
- **Marks:** 4

```cpp
class Solution {
  public:
    vector<int> findPairs(vector<int>& arr) {
        // code here
        
        int n = arr.size();
        unordered_map<long long, pair<int, int>> map;
        vector<int> ans = {-1, -1, -1, -1};
        
        for (int i = 0; i < n; i++) {
            for (int j = i +1; j < n; j++) {
                long long sum = arr[i] + arr[j];
                
                if (map.count(sum)) {
                    auto [a, b] = map[sum];
                    
                    if (a != i && a != j && b != i && b != j) {
                        vector<int>temp = {a, b, i, j};
                        
                        if (ans[0] == -1 || temp < ans) {
                            ans = temp;
                        }
                    }
                } else {
                    map[sum] = {i, j};
                }
            }
        }
        
        return ans;
        
    }
};
```

*Generated on: 11/24/2026, 11:55:44 PM*