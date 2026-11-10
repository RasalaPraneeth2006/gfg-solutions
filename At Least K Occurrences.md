## 01. At Least K Occurrences

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/first-element-to-occur-k-times5150/1?_gl=1*7dw6bs*_up*MQ..*_gs*MQ..&gclid=Cj0KCQjwlYHBBhD9ARIsALRu09pbgqNAyqVxhcm8IAnjUTMlLJhIC1w5aC7xa3QAQYivF9iTVK4woaUaAsehEALw_wcB&gbraid=0AAAAAC9yBkCuY1XCOe54dwAzS3bpeogBG)

### Problem Description

**Task:** Given an array arr[] and an integer k, find the first element that occurs at least k times in the array.If multiple elements satisfy the condition, return the element whose k-th occurrence appears earliest in the array.If no element occurs at least k times, return -1.Examples:Input: arr[] = [1, 7, 4, 3, 4, 8, 7], k = 2

#### Examples

##### Example 1

- **Output:**
```text
4
```
- **Explanation:** Both 7 and 4 occur twice. However, 4 reaches its second occurrence before 7, so the answer is 4.Input: arr[] = [3, 1, 3, 4, 5, 1, 3, 3, 5, 4], k = 3Output: 3Explanation: The element 3 is the only element that occurs at least 3 times in the array.Input: arr[] = [10, 8, 2], k = 10Output: -1Explanation: No element occurs at least 10 times in the array.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(n)

### Accepted Solutions (1)

#### Solution 1 (C++)

- **Submitted:** 2026-11-10 23:40:43
- **Status:** Correct
- **Marks:** 2

```cpp
class Solution {
  public:
    int firstElementKTime(vector<int>& arr, int k) {
        // code here
        unordered_map<int,int>m;
        int n = arr.size();
        for(int val:arr)if((++m[val])==k)return val;
        return -1;
    }
};
```

*Generated on: 11/10/2026, 11:41:05 PM*