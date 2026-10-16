## 01. Maximum Without 3 Consecutive Set Bits

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/geek-hates-too-many-1s--170647/1)

### Problem Description

**Task:** Given a non-negative integer n, you can only change a set bit (1) to an unset bit (0). Find the maximum possible value of n such that its binary representation does not contain three consecutive set bits (111) after performing zero or more allowed operations.Examples:Input: n = 2

#### Examples

##### Example 1

- **Output:**
```text
6
```
- **Explanation:** The binary representation of 7 is 111, which contains three consecutive set bits. Changing the rightmost set bit to 0 gives: 111 - > 110. Thus, the maximum possible value is 6.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(1)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (1)

#### Solution 1 (C++)

- **Submitted:** 2026-10-16 22:27:26
- **Status:** Correct
- **Marks:** 4

```cpp
class Solution {
  public:
    int maxValue(int n) {
        // code here
        vector<int>temp(32,0);
        int index=31,cnt=0,res=0;
        while(n){
            temp[index--]=(n%2);
            n/=2;
        }
        for(int i=0;i<32;i++){
            if(temp[i]==1) cnt++;
            else cnt=0;
            if(cnt==3){
                temp[i]=0;
                cnt=0;
            }
        }
        
        long long k=1;
        for(int i=31;i>=0;i--){
            res+=(temp[i]*k);
            k*=2;
        }
        return res;
        
    }
};
```

*Generated on: 10/16/2026, 10:27:54 PM*