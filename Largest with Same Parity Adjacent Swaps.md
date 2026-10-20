## 01. Largest with Same Parity Adjacent Swaps

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/even-swap/1?_gl=1*gfgiks*_up*MQ..*_gs*MQ..&gclid=Cj0KCQjwlYHBBhD9ARIsALRu09pbgqNAyqVxhcm8IAnjUTMlLJhIC1w5aC7xa3QAQYivF9iTVK4woaUaAsehEALw_wcB&gbraid=0AAAAAC9yBkCuY1XCOe54dwAzS3bpeogBG)

### Problem Description

**Task:** Given an array arr[], you are allowed to swap two adjacent elements, arr[i] and arr[i + 1] only if their sum is even. Find the lexicographically largest array that can be obtained by performing this operation any number of times, including zero times. Note: An array X is lexicographically larger than another array Y if, at the first position where they differ, X has the larger element.Examples:Input: arr[] = [1, 3, 5]Output: [5, 3, 1]

#### Examples

##### Example 1

- **Output:**
```text
[3, 1, 4, 2]Explanation: [1, 3, 4, 2], [1, 3, 2, 4], [3, 1, 2, 4] and [3, 1, 4, 2] are all possible, among which the last one is lexicographically largest one.
```
- **Explanation:** We can swap any adjacent pair as all have even sum. All possible obtainable arrays are [1, 3, 5], [1, 5, 3], [3, 1, 5], [3, 5, 1], [5, 1, 3] and [5, 3, 1] The array [5, 3, 1] is lexicographically largest.Input: arr[] = [1, 3, 4, 2]

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n log n)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (1)

#### Solution 1 (C++)

- **Submitted:** 2026-10-20 21:45:51
- **Status:** Correct
- **Marks:** 4

```cpp
class Solution {
public:
    vector<int> lexicographicallyLargest(vector<int> &arr) {
        int i = 0;
        while (i < arr.size()) {
            int j = i;
            while (j + 1 < arr.size() && (arr[j] + arr[j + 1]) % 2 == 0) {
                j++;
            }
            sort(arr.begin() + i, arr.begin() + j + 1, greater<int>());
            i = j + 1;
        }
        return arr;
    }
};
```

*Generated on: 10/20/2026, 9:47:08 PM*