## 01. Count Group Occurrences

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/count-the-characters1821/1?_gl=1*gk9u2e*_up*MQ..*_gs*MQ..&gclid=Cj0KCQjwlYHBBhD9ARIsALRu09pbgqNAyqVxhcm8IAnjUTMlLJhIC1w5aC7xa3QAQYivF9iTVK4woaUaAsehEALw_wcB&gbraid=0AAAAAC9yBkCuY1XCOe54dwAzS3bpeogBG)

### Problem Description

**Task:** Given a string s and an integer k, count the number of distinct characters that appear in exactly k groups in the string.A group is defined as one or more consecutive occurrences of the same character. For example, in the string "aaabbcca", the groups are "aaa", "bb", "cc" and "a".Examples:Input: s = "abc", k = 1Output: 3Explanation: The characters 'a', 'b' and 'c' each appear in exactly one group.Input: s = "geeksforgeeks", k = 2Output: 4Explanation: The characters 'g', 'e', 'k' and 's' each appear in exactly two groups.Input: s = "aaaaa", k = 2Output: 0Explanation: The character 'a' appears in only one group, so no character appears in exactly two groups.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (1)

#### Solution 1 (C++)

- **Submitted:** 2026-11-09 22:39:45
- **Status:** Correct
- **Marks:** 2

```cpp
class Solution {
  public:
    int getCount(string &s, int k) {
        // code here
        unordered_map<char, int> countGroup;
        
        char prevChar;
        
        int ans = 0;
        
        for (auto i : s) {
            if (prevChar != i) {
                countGroup[i]++;
                prevChar = i;
            }
        }
        
        for (auto i : countGroup) {
            if (i.second == k) {
                ans++;
            }
        }
        
        return ans;
    }
};
```

*Generated on: 11/9/2026, 10:40:11 PM*