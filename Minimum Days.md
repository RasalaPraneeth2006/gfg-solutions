## 01. Minimum Days

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/minimum-days--170646/1?_gl=1*1ctu6jm*_up*MQ..*_gs*MQ..&gclid=Cj0KCQjwlYHBBhD9ARIsALRu09pbgqNAyqVxhcm8IAnjUTMlLJhIC1w5aC7xa3QAQYivF9iTVK4woaUaAsehEALw_wcB&gbraid=0AAAAAC9yBkCuY1XCOe54dwAzS3bpeogBG)

### Problem Description

**Task:** Given a string s of length n containing only lowercase English letters, and a permutation array p[] of length n containing integers from 0 to n - 1. On the (i + 1)th day, the character at index p[i] in the string is replaced with '?'. For example:On day 1, replace s[p[0]] with '?'.On day 2, replace s[p[1]] with '?'.On day 3, replace s[p[2]] with '?'.And so on.Find the minimum number of days required so that no two adjacent characters in s are equal, unless at least one of them is '?'.Formally, for every index i (0 <= i < n - 1), the string must satisfy: If s[i] ! = '?' and s[i+1] ! = '?', then s[i] ! = s[i+1].Examples:Input: s = "aabb", p = [2, 1, 3, 0]

#### Examples

##### Example 1

- **Output:**
```text
0 The initial string "abca" already satisfies the condition without replacing any characters.
```

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(n) [Note: For CPP - O(1)]

### Accepted Solutions (1)

#### Solution 1 (C++)

- **Submitted:** 2026-11-05 23:52:30
- **Status:** Correct
- **Marks:** 4

```cpp
class Solution {
  public:
    int getMinimumDays(string &s, vector<int> &p) {
        // code here
        int days = 0;
        int n = p.size();
        
        for(int i=0;i<n;i++){
            
            int idx = p[i];
            char r = (idx+1<n)?s[idx+1]:'$';
            char l = (idx-1>=0)?s[idx-1]:'$';
            
            if(r==s[idx] || l==s[idx]){
                s[idx] = '?';
                days=i+1;
            }
        }
        
        return days;
    }
};
```

*Generated on: 11/5/2026, 11:52:50 PM*