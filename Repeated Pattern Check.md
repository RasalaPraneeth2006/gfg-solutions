## 01. Repeated Pattern Check

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/the-pattern-matcher/1?_gl=1*1u07so*_up*MQ..*_gs*MQ..&gclid=Cj0KCQjwlYHBBhD9ARIsALRu09pbgqNAyqVxhcm8IAnjUTMlLJhIC1w5aC7xa3QAQYivF9iTVK4woaUaAsehEALw_wcB&gbraid=0AAAAAC9yBkCuY1XCOe54dwAzS3bpeogBG)

### Problem Description

**Task:** Given a string s made of two characters of 'x' and 'y'. The task is to verify whether s is made by concatenating substrings that follow the pattern x^ny^n (equal number of y's follow equal number of x's).Examples:Input: s = "xxyyxy" Output: trueExplanation: The string can be split into "xxyy" + "xy". Both substrings contain an equal number of consecutive 'x' and 'y' characters.Input: s = "xyx"Output: falseExplanation: The last 'x' cannot form a valid substring because it is not followed by a matching 'y'.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(|s|)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (1)

#### Solution 1 (C++)

- **Submitted:** 2026-11-17 23:13:04
- **Status:** Correct
- **Marks:** 2

```cpp
class Solution {
  public:
    virtual bool findPattern(string& s){
      int count=0;
      int n=s.size();
      
      int i=0;
      while(i<n){
       while(i<n && s[i]=='x') { count++; i++; }
       
       while(i<n && s[i]=='y') { 
         count--; i++; 
         if(count<0) return false;  
       }
       
       if(count) return false;
       
      }
      
      
      return count==0;
    }
};
```

*Generated on: 11/17/2026, 11:13:27 PM*