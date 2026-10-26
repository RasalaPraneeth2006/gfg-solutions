## 01. Minimize Max Min Diff with Subarray Removal

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/minimize-the-difference/1?_gl=1*9rucvf*_up*MQ..*_gs*MQ..&gclid=Cj0KCQjwlYHBBhD9ARIsALRu09pbgqNAyqVxhcm8IAnjUTMlLJhIC1w5aC7xa3QAQYivF9iTVK4woaUaAsehEALw_wcB&gbraid=0AAAAAC9yBkCuY1XCOe54dwAzS3bpeogBG)

### Problem Description

**Task:** You are given an array arr[] of size n. You need to remove a subarray of size k , such that the difference between the maximum and minimum values of the remaining array is minimized. Find the minimum value obtained after performing the operation of the removal of the subarray.Examples:Input: arr = [1, 2, 3, 4, 5], k = 3 Output: 1Explanation: We remove first subarray of length 3, the remaining array is [4,5] and the difference of maximum and minimum element is 1 i.e 5 - 4 = 1Input: arr = [2, 3, 1, 4, 6, 7], k = 3Output: 2Explanation: If we remove the subarray [2,3,1] then remaining array is [4,6,7] and the difference = 7-4 = 3If we remove the subarray [3,1,4] then remaining array is [2,6,7] and the difference = 7-2 = 5If we remove the subarray [1,4,6] then remaining array is [2,3,7] and the difference = 7-2 = 5If we remove the subarray [4,6,7] then remaining array is [2,3,1] and the difference = 3-1 = 2So the answer is min(3,5,5,2) = 2

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(n)

### Accepted Solutions (1)

#### Solution 1 (Java)

- **Submitted:** 2026-10-26 23:40:09
- **Status:** Correct
- **Marks:** 4

```java
class Solution {
    public int minDiff(int k, int[] arr) {
        int n = arr.length;

        // If k >= n, removing the whole array leaves nothing (difference is 0)
        if (k >= n) return 0;

        int[] prefixMax = new int[n];
        int[] prefixMin = new int[n];
        int[] suffixMax = new int[n];
        int[] suffixMin = new int[n];

        prefixMax[0] = arr[0];
        prefixMin[0] = arr[0];
        for (int i = 1; i < n; i++) {
            prefixMax[i] = Math.max(prefixMax[i - 1], arr[i]);
            prefixMin[i] = Math.min(prefixMin[i - 1], arr[i]);
        }

        suffixMax[n - 1] = arr[n - 1];
        suffixMin[n - 1] = arr[n - 1];
        for (int i = n - 2; i >= 0; i--) {
            suffixMax[i] = Math.max(suffixMax[i + 1], arr[i]);
            suffixMin[i] = Math.min(suffixMin[i + 1], arr[i]);
        }

        int ans = Integer.MAX_VALUE;

        // Try removing every subarray of size k starting at index i
        for (int i = 0; i <= n - k; i++) {
            int currentMax = Integer.MIN_VALUE;
            int currentMin = Integer.MAX_VALUE;

            // Include prefix portion before the removed window
            if (i > 0) {
                currentMax = Math.max(currentMax, prefixMax[i - 1]);
                currentMin = Math.min(currentMin, prefixMin[i - 1]);
            }

            // Include suffix portion after the removed window
            if (i + k < n) {
                currentMax = Math.max(currentMax, suffixMax[i + k]);
                currentMin = Math.min(currentMin, suffixMin[i + k]);
            }

            ans = Math.min(ans, currentMax - currentMin);
        }

        return ans;
    }
}
```

*Generated on: 10/26/2026, 11:40:30 PM*