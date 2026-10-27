## 01. Maximum Weight Transformation of String

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/maximum-weight-transformation-of-a-given-string3551/1?_gl=1*1conzq3*_up*MQ..*_gs*MQ..&gclid=Cj0KCQjwlYHBBhD9ARIsALRu09pbgqNAyqVxhcm8IAnjUTMlLJhIC1w5aC7xa3QAQYivF9iTVK4woaUaAsehEALw_wcB&gbraid=0AAAAAC9yBkCuY1XCOe54dwAzS3bpeogBG)

### Problem Description

**Task:** Given a string s consisting only of the characters 'A' and 'B', you can toggle any character. A toggle changes 'A' to 'B' or 'B' to 'A'.The weight of a string is calculated using the following rules:An alternating adjacent pair ("AB" or "BA") contributes 4 to the weight. Each character can belong to at most one pair, so the pairs must not overlap.Every character that does not belong to any pair contributes 1 to the weight.Each toggle performed decreases the total weight by 1.Therefore, Weight = Weight of alternating adjacent pairs + Weight of characters that do not belong to any pair - Number of TogglesYou can toggle characters to make adjacent characters different and form pairs. Find the maximum possible weight obtainable from the string by choosing pairs and toggling characters optimally.Examples:Input: s = "AA"

#### Examples

##### Example 1

- **Output:**
```text
5
```
- **Explanation:** Possible transformations are "ABB", "ABA", "AAB", "AAA", "BBB", "BBA", "BAB" and "BAA". The original string "ABB" contains the alternating adjacent pair "AB", contributing 4 to the weight, while the remaining character 'B' contributes 1. No toggles are required. Therefore, the maximum weight is 4 + 1 = 5.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(n)

### Accepted Solutions (1)

#### Solution 1 (C++)

- **Submitted:** 2026-10-27 23:55:15
- **Status:** Correct
- **Marks:** 4

```cpp
class Solution {
  public:
    int getMaxWeight(string &s) {
        int n = s.size();
        if (n == 0) return 0;
        int m = n - 1;
        vector<int> gain(m);
        for (int i = 0; i < m; i++) {
            gain[i] = (s[i] == s[i + 1] ? 1 : 2);
        }
        vector<int> dp(m + 1, 0);
        for (int i = 1; i <= m; i++) {
            dp[i] = max(dp[i - 1], (i >= 2 ? dp[i - 2] : 0) + gain[i - 1]);
        }
        return n + dp[m];
    }
};
```

*Generated on: 10/27/2026, 11:55:35 PM*