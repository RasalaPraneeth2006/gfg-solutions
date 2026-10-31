## 01. C++ Solution || Easy Approach and Step by Step Explanation

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/bird-and-maximum-fruit-gathering0509/1?_gl=1*d4jhvr*_up*MQ..*_gs*MQ..&gclid=Cj0KCQjwlYHBBhD9ARIsALRu09pbgqNAyqVxhcm8IAnjUTMlLJhIC1w5aC7xa3QAQYivF9iTVK4woaUaAsehEALw_wcB&gbraid=0AAAAAC9yBkCuY1XCOe54dwAzS3bpeogBG)

### Problem Description

**Task:** A delivery agent has to deliver packages at locations arranged in a line. The number of packages at the ith location is given by arr[i]. The agent can start at any location and can only visit consecutive locations.Visiting each location takes 1 unit of time.Given arr[] and totalTime, find the maximum number of packages the agent can deliver within totalTime.Examples:Input: arr[] = [2, 1, 3, 5, 0, 1, 4], totalTime = 3

#### Examples

##### Example 1

- **Output:**
```text
8
```
- **Explanation:** The agent can visit two consecutive locations. Starting from the second location, it delivers arr[1] + arr[2] = 6 + 2 = 8 packages. Starting from the fourth location gives arr[3] + arr[4] = 5 + 3 = 8 packages. Hence, the maximum is 8 packages.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (1)

#### Solution 1 (C++)

- **Submitted:** 2026-10-31 23:53:03
- **Status:** Correct
- **Marks:** 2

```cpp
class Solution {
  public:
    int maxPackages(vector<int>& arr, int totalTime) {
        // code here
        int currsum=0;
        
        int i=0;
        for(;i<totalTime && i<arr.size();i++){
            currsum+=arr[i];
        }
        int maxi=currsum;
        for(int j=totalTime;j<arr.size();j++){
            currsum-=arr[j-totalTime];
            currsum+=arr[j];
            maxi=max(currsum,maxi);
        }
        return maxi;
    }
};
```

*Generated on: 10/31/2026, 11:53:34 PM*