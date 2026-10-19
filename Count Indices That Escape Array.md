## 01. Count Indices That Escape Array

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/good-stones--170647/1?_gl=1*bh9uu1*_up*MQ..*_gs*MQ..&gclid=Cj0KCQjwlYHBBhD9ARIsALRu09pbgqNAyqVxhcm8IAnjUTMlLJhIC1w5aC7xa3QAQYivF9iTVK4woaUaAsehEALw_wcB&gbraid=0AAAAAC9yBkCuY1XCOe54dwAzS3bpeogBG)

### Problem Description

**Task:** Given an array arr[], where arr[i] represents the exact number of steps to move from index i. An index is considered good if repeatedly following the jumps eventually takes you outside the array. Otherwise, if the jumps result in an infinite loop, the index is considered bad. A positive value indicates a move to the rightA negative value indicates a move to the left.A 0 value means no move and considered bad.Return the number of good indices.Examples:Input: [2, 3, -1, 2, -2, 4, 1]

#### Examples

##### Example 1

- **Output:**
```text
3
```
- **Explanation:** Indices 3, 5, and 6 are good because their jump sequences eventually leave the array. Indices 1, 2, and 4 form a cycle, while index 0 eventually enters this cycle through index 2. Hence, the total number of good indices is 3.

##### Example 2

- **Input:**
```text
[1, 0, -3, 0, -5, 0]
```
- **Output:**
```text
2
```
- **Explanation:** Indices 2 and 4 are good because their jumps take them outside the array. Indices 1, 3, and 5 are bad because their jumps are zero. Index 0 is also bad because it jumps to index 1, which is a dead end. Hence, the total number of good indices is 2.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(n)

### Accepted Solutions (1)

#### Solution 1 (C++)

- **Submitted:** 2026-10-19 21:09:46
- **Status:** Correct
- **Marks:** 4

```cpp
class Solution {
  public:
    int count=0;
    void dfs(unordered_map<int,vector<int>>&graph,int node){
        count++;
        for(int i:graph[node]){
            dfs(graph,i);
        }
        return;
    }
    int goodIndices(vector<int> &arr) {
        // code here
        //we need to eleminate the cycles
        //consider each one as node
        //then cycle topo sort to get the non cycle indexes
        //from outside to inside which index can be visited they are safe like evental 
        //safe state
        //reverse the edges
        //adj list
        count=0;
        int n=arr.size();
        vector<int>adj(n);
        unordered_map<int,vector<int>>graph;
        for(int i=0;i<n;i++){
            adj[i]=(arr[i]+i>=n or arr[i]+i<0)?n:arr[i]+i;
            
        }
        //formed the edges reverse the edge list
        for(int i=0;i<n;i++){
            graph[adj[i]].push_back(i);
        }
        //from the outer node how many are reachble nodes no need of visted as 
        //dag from the node n only needed
        dfs(graph,n);
        
        return count-1;
        
        
        
    
    }
};
```

*Generated on: 10/19/2026, 9:28:27 PM*