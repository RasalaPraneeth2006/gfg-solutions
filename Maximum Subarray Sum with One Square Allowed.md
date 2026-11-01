## 01. Maximum Subarray Sum with One Square Allowed

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/maximum-sum-subarray--143510/1?_gl=1*nt7ac5*_up*MQ..*_gs*MQ..&gclid=Cj0KCQjwlYHBBhD9ARIsALRu09pbgqNAyqVxhcm8IAnjUTMlLJhIC1w5aC7xa3QAQYivF9iTVK4woaUaAsehEALw_wcB&gbraid=0AAAAAC9yBkCuY1XCOe54dwAzS3bpeogBG)

### Problem Description

**Task:** Given an integer array arr[], find the maximum subarray sum by squaring at most one element.Examples:Input: arr[] = [-1, -2, 3, -2, 3]Output: 10Explanation: The subarray {3, -2, 3} with squaring -2 will give the maximum sum as 3 + 4 + 3 = 10.Input: arr[] = [-4, -4, -2, 5, 2, -1]Output: 27Explanation: The subarray {5, 2} with squaring 5 will give a maximum sum of 25 + 2 = 27.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (1)

#### Solution 1 (C++)

- **Submitted:** 2026-11-01 23:58:42
- **Status:** Correct
- **Marks:** 4

```cpp
class Solution {
  public:
    int maximumSubarray(vector<int>& arr) {
        int n = arr.size();
        int fAns = INT_MIN;
        int activeSum = 0;
        int dormantSum = 0;
        for(int i=0;i<n;i++){
            activeSum = max(activeSum + arr[i], dormantSum + arr[i] * arr[i]);
            dormantSum = max(dormantSum + arr[i], 0);
            fAns = max(fAns, max(activeSum, dormantSum));
        }
        return fAns;
    }
};
```

*Generated on: 11/1/2026, 11:59:44 PM*