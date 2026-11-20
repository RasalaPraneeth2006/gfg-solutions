## 01. Min Flips for Alternate

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/min-number-of-flips3210/1?_gl=1*9a5ujq*_up*MQ..*_gs*MQ..&gclid=Cj0KCQjwlYHBBhD9ARIsALRu09pbgqNAyqVxhcm8IAnjUTMlLJhIC1w5aC7xa3QAQYivF9iTVK4woaUaAsehEALw_wcB&gbraid=0AAAAAC9yBkCuY1XCOe54dwAzS3bpeogBG)

### Problem Description

**Task:** Given a binary string s, we can flip any bit (change 0 to 1 or 1 to 0) to make the string alternating. A string is called alternating if no two adjacent characters are the same. Find the minimum number of bit flips required to make the string alternating.Examples:Input: s = "001"

#### Examples

##### Example 1

- **Output:**
```text
1
```
- **Explanation:** Flip the bit at index 0 from 0 to 1 to obtain "101", which is an alternating binary string. Hence, the minimum number of flips required is 1.

##### Example 2

- **Input:**
```text
s = "0001010111"
```
- **Output:**
```text
2
```
- **Explanation:** Flip the bit at indices 1 and 8 to obtain "0101010101", which is an alternating binary string. Hence, the minimum number of flips required is 2.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (1)

#### Solution 1 (C++)

- **Submitted:** 2026-11-20 22:58:28
- **Status:** Correct
- **Marks:** 2

```cpp
class Solution {
  public:
    int minFlips(string &s) {
        // code here
        bool flag1 = 0;
        bool flag2 = 1;
        int n = s.size();
        int ans1 = 0;
        int ans2 = 0;
        
        
        for(int i=0;i<n;i++){
            
            int c = s[i]-'0';
            if(c!=flag1)ans1++;
            if(c!=flag2)ans2++;
            flag1 = !flag1;
            flag2 = !flag2;
        }
        
        return min(ans1,ans2);
    }
};
```

*Generated on: 11/20/2026, 10:58:47 PM*