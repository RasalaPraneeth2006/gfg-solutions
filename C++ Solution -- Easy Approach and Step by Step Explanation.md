## 01. C++ Solution || Easy Approach and Step by Step Explanation

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/pairs-violating-bst-property--212515/1?_gl=1*hqm8yq*_up*MQ..*_gs*MQ..&gclid=Cj0KCQjwlYHBBhD9ARIsALRu09pbgqNAyqVxhcm8IAnjUTMlLJhIC1w5aC7xa3QAQYivF9iTVK4woaUaAsehEALw_wcB&gbraid=0AAAAAC9yBkCuY1XCOe54dwAzS3bpeogBG)

### Problem Description

**Task:** Given root of a binary tree in which all node values are distinct, count pairs of nodes that violate any of the following Binary Search Tree (BST) properties. All values in the left subtree are strictly smaller.All values in the right subtree are strictly greater.Examples:Input: root[] = [10, 50, 40, N, N, 20, 30]Output: 5

#### Examples

##### Example 1

- **Explanation:** There are total 10 pairs (80, 30), (80, 60), (80, 50), (30, 60), (40, 70), (40, 30), (40, 50), (70, 30), (70, 60), (70, 50) which violate the BST properties.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n log n)
- **Expected Auxiliary Space Complexity:** O(n)

### Accepted Solutions (1)

#### Solution 1 (Java)

- **Submitted:** 2026-10-23 21:58:17
- **Status:** Correct
- **Marks:** 4

```java
class Solution {
    private List<Integer> elements;
    private int pairs;

    public int pairsViolatingBST(Node root) {
        // code here
        elements = new ArrayList<>();
        pairs = 0;

        reverseInorder(root);

        return pairs;
    }

    // Right -> Root -> Left (descending order of inorder)
    private void reverseInorder(Node root) {
        if (root == null) {
            return;
        }

        reverseInorder(root.right);

        int count = countSmaller(root.data);
        elements.add(count, root.data);  // sorted order maintain hota hai
        pairs += count;

        reverseInorder(root.left);
    }

    // Kitne elements target se strictly chhote hain (binary search)
    private int countSmaller(int target) {
        int l = 0;
        int r = elements.size() - 1;
        int ans = -1;

        while (l <= r) {
            int mid = l + (r - l) / 2;

            if (elements.get(mid) >= target) {
                r = mid - 1;
            } else {
                ans = mid;
                l = mid + 1;
            }
        }
        
        return ans + 1;
    }
}
```

*Generated on: 10/23/2026, 9:58:41 PM*