## 01. C++ Solution || Easy Approach and Step by Step Explanation

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/bbt-counter4914/1?_gl=1*wat43o*_up*MQ..*_gs*MQ..&gclid=Cj0KCQjwlYHBBhD9ARIsALRu09pbgqNAyqVxhcm8IAnjUTMlLJhIC1w5aC7xa3QAQYivF9iTVK4woaUaAsehEALw_wcB&gbraid=0AAAAAC9yBkCuY1XCOe54dwAzS3bpeogBG)

### Problem Description

**Task:** Given a height h, find the maximum number of distinct balanced binary trees of height exactly h.A binary tree is balanced if, for every node, the heights of its left and right subtrees differ by at most 1. A tree with a single node has height 1. An empty tree has height 0.Note: Since the answer can be very large, return it modulo 10⁹ + 7.Examples:Input: h = 1Output: 1Explanation: Only one tree of height 1 exists i.e. a single node.Input: h = 2

#### Examples

##### Example 1

- **Output:**
```text
3
```
- **Explanation:** 3 distinct balanced trees of height 2 exist.

##### Example 2

- **Input:**
```text
h = 3
```
- **Output:**
```text
15
```
- **Explanation:** 15 distinct balanced trees of height 3 exist.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(h)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (1)

#### Solution 1 (C++)

- **Submitted:** 2026-11-06 23:20:23
- **Status:** Correct
- **Marks:** 2

```cpp
class Solution {
  public:
    int countBT(int h) {
        long long MOD = 1e9 + 7;
        vector<long long> dp(h + 1, 1);

        for (int i = 2; i <= h; i++) {
            long long prev1 = dp[i - 1];
            long long prev2 = dp[i - 2];
            dp[i] = (prev1 * (prev1 + 2 * prev2)) % MOD;
        }

        return dp[h];
    }
};
```

*Generated on: 11/6/2026, 11:20:45 PM*