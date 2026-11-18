## 01. Sort in Specific Order

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/sort-in-specific-order2422/1?_gl=1*16s7923*_up*MQ..*_gs*MQ..&gclid=Cj0KCQjwlYHBBhD9ARIsALRu09pbgqNAyqVxhcm8IAnjUTMlLJhIC1w5aC7xa3QAQYivF9iTVK4woaUaAsehEALw_wcB&gbraid=0AAAAAC9yBkCuY1XCOe54dwAzS3bpeogBG)

### Problem Description

**Task:** Given an array arr[] of positive integers. Your need to sort them so that The first part of the array contains odd numbers sorted in descending order.The rest of the portion contains even numbers sorted in ascending order.Examples:Input: arr[] = [1, 2, 3, 5, 4, 7, 10]

#### Examples

##### Example 1

- **Output:**
```text
[7, 5, 3, 1, 0, 2, 4]Explanation: 7, 5, 3, 1 are odd numbers in descending order and 0, 2, 4 are even numbers in ascending order.
```
- **Explanation:** 7, 5, 3, 1 are odd numbers in descending order and 2, 4, 10 are even numbers in ascending order.Input: arr[] = [0, 4, 5, 3, 7, 2, 1]

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n log n)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (1)

#### Solution 1 (C++)

- **Submitted:** 2026-11-19 00:04:21
- **Status:** Correct
- **Marks:** 4

```cpp
class Solution {
  public:
    void sortIt(vector<int>& arr) {
        // code here
        int n=arr.size();
        vector<int >ans;
        sort(arr.begin(),arr.end());
        
        for(int i=arr.size()-1;i>=0;i--){
            if(arr[i]%2!=0){
                ans.push_back(arr[i]);
            }
        }
        
        for(int i=0;i<arr.size();i++){
            if(arr[i]%2==0){
                ans.push_back(arr[i]);
            }
        }
        
        arr.clear();
        
        arr=ans;
    }
};
```

*Generated on: 11/19/2026, 12:04:52 AM*