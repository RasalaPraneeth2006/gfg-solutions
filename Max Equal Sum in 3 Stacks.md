## 01. Max Equal Sum in 3 Stacks

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/find-maximum-equal-sum-of-three-stacks/1?_gl=1*1upj601*_up*MQ..*_gs*MQ..&gclid=Cj0KCQjwlYHBBhD9ARIsALRu09pbgqNAyqVxhcm8IAnjUTMlLJhIC1w5aC7xa3QAQYivF9iTVK4woaUaAsehEALw_wcB&gbraid=0AAAAAC9yBkCuY1XCOe54dwAzS3bpeogBG)

### Problem Description

**Task:** Given three stacks s1, s2, and s3, represented by arrays where the first element of each array represents the top of the corresponding stack.Find the maximum possible equal sum(sum of all elements) of all three stacks by removing zero or more elements from the top of each stack.If it is not possible to make the sum of all three stacks equal, return 0.Examples:Input: s1 = [3, 2, 1, 1, 1], s2 = [4, 3, 2], s3 = [2, 5, 4, 1]Output: 5Explanation: Remove 3 from s1, 4 from s2, and 2, 5 from s3. The remaining sums of all three stacks are equal to 5.Input: s1 = [4,7], s2 = [10], s3 = [1,2,3]

#### Examples

##### Example 1

- **Output:**
```text
0
```
- **Explanation:** It is not possible to make the sums of all three stacks equal by removing elements from their tops.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n1 + n2 + n3)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (1)

#### Solution 1 (C++)

- **Submitted:** 2026-11-14 23:53:22
- **Status:** Correct
- **Marks:** 4

```cpp
class Solution {
  public:
    int maxEqualSum(vector<int> &s1, vector<int> &s2, vector<int> &s3) {
        // code here
        
        int sum1 = accumulate(begin(s1), end(s1), 0);
        int sum2 = accumulate(begin(s2), end(s2), 0);
        int sum3 = accumulate(begin(s3), end(s3), 0);
        
        int n1 = s1.size();
        int n2 = s2.size();
        int n3 = s3.size();
        
        int i = 0;
        int j = 0;
        int k = 0;
        
        // This Loop will run only max(n1, n2, n3) times
        while (true) {
            
            if (sum1 == sum2 && sum2 == sum3) {
                return sum1;
            }
            
            if (i == n1 && j == n2 && k == n3) {
                break;
            }
            
            
            int maxSum = max({sum1, sum2, sum3});
            
            if (sum1 == maxSum) {
                sum1 -= s1[i];
                if (i < n1) i++;
            } else if (sum2 == maxSum) {
                sum2 -= s2[j];
                if (j < n2) j++;
            } else {
                sum3 -= s3[k];
                if (k < n3) k++;
            }
        }
        
        return 0;
    }
};
```

*Generated on: 11/14/2026, 11:53:44 PM*