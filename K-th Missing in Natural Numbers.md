## 01. K-th Missing in Natural Numbers

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/k-th-missing-element-in-natural-numbers/1?_gl=1*76gl2s*_up*MQ..*_gs*MQ..&gclid=Cj0KCQjwlYHBBhD9ARIsALRu09pbgqNAyqVxhcm8IAnjUTMlLJhIC1w5aC7xa3QAQYivF9iTVK4woaUaAsehEALw_wcB&gbraid=0AAAAAC9yBkCuY1XCOe54dwAzS3bpeogBG)

### Problem Description

**Task:** Given an array arr[] of distinct positive integers and a positive integer k. Consider an infinite sequence of natural numbers starting from 1. The task is to remove all elements present in arr[] from this sequence.Find the k-th smallest number in the remaining sequence.Note: Your solution must run in O(1) auxiliary space.Examples:Input: arr[] = [1, 9, 5, 2], k = 6Output: 10Explanation: After removing [1, 2, 5, 9] from the natural numbers, the remaining sequence is: 3, 4, 6, 7, 8, 10, 11, .... and so on. The 6th number in this sequence is 10, so the answer is 10.Input: arr[] = [1, 2, 3, 4], k = 1Output: 5Explanation: After removing [1, 2, 3, 4] from the natural numbers, the remaining sequence is: 5, 6, 7, .... and so on. The 1st number in the sequence is 5, so the answer is 5.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n log n)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (2)

#### Solution 1 (Java)

- **Submitted:** 2026-11-16 23:07:24
- **Status:** Correct
- **Marks:** 0

```java
class Solution {
    public int findKthSmall(int[] arr, int k) {
        // code here
        Arrays.sort(arr);
        int j=arr.length+k;
        int b=0;
        for(int i=1;i<=j;i++){
            if(b<arr.length && arr[b]==i){
                b++;
            }
            else{
                k--;
            }
            if(k==0){
                return i;
            }
        }
        return -1;
    }
}
```

#### Solution 2 (Java)

- **Submitted:** 2026-11-16 23:06:34
- **Status:** Correct
- **Marks:** 4

```java
class Solution {
  public:
    int findKthSmall(vector<int>& arr, int k) {
        int start = k, end = k + arr.size();
        
        while(start < end){
            int mid = start + (end - start) / 2;
            int miss = mid;
            for(int v: arr)
                if(v <= mid)
                    miss--;
            if(miss < k)
                start = mid + 1;
            else
                end = mid;
        }
        
        return start;
    }
};
```

*Generated on: 11/16/2026, 11:07:51 PM*