## 01. Common Nodes in Two BSTs

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/print-common-nodes-in-bst/1?_gl=1*1dg9ska*_up*MQ..*_gs*MQ..&gclid=Cj0KCQjwlYHBBhD9ARIsALRu09pbgqNAyqVxhcm8IAnjUTMlLJhIC1w5aC7xa3QAQYivF9iTVK4woaUaAsehEALw_wcB&gbraid=0AAAAAC9yBkCuY1XCOe54dwAzS3bpeogBG)

### Problem Description

**Task:** Given the roots r1 and r2 of two Binary Search Trees (BST), find all nodes that are present in both trees i.e. the intersection nodes of the two BSTs.Return the common node values in sorted order.Examples:Input: r1 = [5, 1, 10, 0, 4, 7, N, N, N, N, N, N, 9], r2 = [10, 7, 20, 4, 9, N, N] Output: [4, 7, 9, 10]Explanation: The values present in both BSTs are 4, 7, 9, and 10. Hence, the answer is [4, 7, 9, 10].Input: r1 = [10, 2, 11, 1, 3, N, N], r2 = [2, 1, 3]Output: [1, 2, 3]Explanation: The values 1, 2, and 3 are present in both BSTs. Hence, the answer is [1, 2, 3].

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n1 + n2), where n1 and n2 are the number of nodes in r1 and r2 respectively.
- **Expected Auxiliary Space Complexity:** O(h1 + h2), where h1 and h2 are the heights of r1 and r2 respectively.

### Accepted Solutions (1)

#### Solution 1 (C++)

- **Submitted:** 2026-11-13 23:08:34
- **Status:** Correct
- **Marks:** 4

```cpp
/* Structure of a Binary Search Tree node
class Node {
  public:
    int data;
    Node* left;
    Node* right;

    Node(int val) {
        data = val;
        left = right = nullptr;
    }
};
*/
class Solution {
  public:
    vector<int> findCommon(Node* r1, Node* r2) {
        // code here
        unordered_set<int>st;
        Node* root=r1;
        queue<Node*>q;
        q.push(root);
        
        while(!q.empty()){
            Node* node=q.front();
            q.pop();
            st.insert(node->data);
            if(node->left) q.push(node->left);
            if(node->right) q.push(node->right);
        }
        
        vector<int>ans;
        
        root=r2;
        
        q.push(root);
        
        while(!q.empty()){
            Node* node=q.front();
            q.pop();
            if(st.find(node->data)!=st.end()) ans.push_back(node->data);
            if(node->left) q.push(node->left);
            if(node->right) q.push(node->right);
        }
        
        sort(ans.begin(), ans.end());
        
        return ans;
        
    }
};
```

*Generated on: 11/13/2026, 11:08:52 PM*