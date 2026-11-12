## 01. Closest in BST

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/find-the-closest-element-in-bst/1?_gl=1*jaeqk2*_up*MQ..*_gs*MQ..&gclid=Cj0KCQjwlYHBBhD9ARIsALRu09pbgqNAyqVxhcm8IAnjUTMlLJhIC1w5aC7xa3QAQYivF9iTVK4woaUaAsehEALw_wcB&gbraid=0AAAAAC9yBkCuY1XCOe54dwAzS3bpeogBG)

### Problem Description

**Task:** Given root of a Binary Search Tree (BST) and an integer k, find the minimum absolute difference between k and the value of any node in the BST.Examples:Input: root = [10, 2, 11, 1, 5, N, N, N, N, 3, 6, N, 4], k = 13

#### Examples

##### Example 1

- **Output:**
```text
2
```
- **Explanation:** The node with value 11 is closest to k = 13. So, the minimum absolute difference is |11 - 13| = 2.

##### Example 2

- **Input:**
```text
root = [8, 1, 9, N, 4, N, 10, 3], k = 9
```
- **Output:**
```text
0
```
- **Explanation:** The node with value 9 is closest to k = 9. So, the minimum absolute difference is |9 - 9| = 0.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(h)
- **Expected Auxiliary Space Complexity:** O(h)

### Accepted Solutions (1)

#### Solution 1 (C++)

- **Submitted:** 2026-11-12 22:15:47
- **Status:** Correct
- **Marks:** 4

```cpp
class Solution {
  public:
    int minDiff(Node *root, int k) {
        // code here
        if(root)
        {
            if(root->data == k)
            {
                return 0;
            }
            if(root->data > k)
            {
                return min(root->data - k, minDiff(root->left, k));
            }
            else
            {
                return min(k - root->data, minDiff(root->right, k));
            }
        }
        else
        
        {
            return INT_MAX;
        }
    }
};
```

*Generated on: 11/12/2026, 10:16:05 PM*