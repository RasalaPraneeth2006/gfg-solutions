## 01. Smallest Subarray Sum Greater Than x

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/smallest-subarray-with-sum-greater-than-x5651/1?_gl=1*jfcpe0*_up*MQ..*_gs*MQ..&gclid=Cj0KCQjwlYHBBhD9ARIsALRu09pbgqNAyqVxhcm8IAnjUTMlLJhIC1w5aC7xa3QAQYivF9iTVK4woaUaAsehEALw_wcB&gbraid=0AAAAAC9yBkCuY1XCOe54dwAzS3bpeogBG)

### Problem Description

**Task:** Given an integer x and an array of integers, arr[]. Find the length of the smallest subarray whose sum is strictly greater than x. If no such subarray exists, return 0.Examples:Input: x = 51, arr[] = [1, 4, 45, 6, 0, 19]

#### Examples

##### Example 1

- **Output:**
```text
0
```
- **Explanation:** No subarray has a sum greater than 100. Hence, the answer is 0.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (1)

#### Solution 1 (C++)

- **Submitted:** 2026-11-21 23:59:16
- **Status:** Correct
- **Marks:** 2

```cpp
class Solution {
public:
int smallestSubWithSum(vector<int>& arr, int x) {
 
int n = arr.size();
int minLength = INT_MAX;
int start = 0;
int sum = 0;
for (int end = 0; end<n; end++) {
sum += arr[end];
while (sum>x) {
minLength = min(minLength, end - start + 1);
sum -= arr[start];
start++;
}
 
}
return minLength == INT_MAX ? 0:minLength;
}
};
```

*Generated on: 11/21/2026, 11:59:43 PM*