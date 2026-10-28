## 01. Nth in Concatenated Decimal String

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/nth-character-in-concatenated-decimal-string0245/1?_gl=1*1m3h14l*_up*MQ..*_gs*MQ..&gclid=Cj0KCQjwlYHBBhD9ARIsALRu09pbgqNAyqVxhcm8IAnjUTMlLJhIC1w5aC7xa3QAQYivF9iTVK4woaUaAsehEALw_wcB&gbraid=0AAAAAC9yBkCuY1XCOe54dwAzS3bpeogBG)

### Problem Description

**Task:** Consider a string s formed by concatenating the decimal representations of all positive integers in order:s = "12345678910111213141516171819202122232425262728293031..."Given an integer n, find the nth character (1-based indexing) in the string s.Examples:Input: n = 10

#### Examples

##### Example 1

- **Output:**
```text
'0'
```
- **Explanation:** The 11th character in "12345678910.." is '0'.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(log n)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (1)

#### Solution 1 (C++)

- **Submitted:** 2026-10-28 23:52:27
- **Status:** Correct
- **Marks:** 4

```cpp
class Solution {
  public:
    char nthCharacter(int n) {
        vector<long long> digit(11, 0);
        vector<long long> power(11, -1);

        long long prev = 1;
        long long curr = 10;
        int count = 1;

        for (int i = 1; i <= 10; i++) {
            digit[i] = (curr - prev) * count + digit[i - 1];
            power[i] = prev;
            prev = curr;
            curr *= 10;
            count++;
        }

        long long l = 1;
        long long r = n;

        while (l <= r) {
            long long mid = l + (r - l) / 2;
            string t = to_string(mid);
            int m = t.size();

            long long cnt = (mid - power[m] + 1) * m + digit[m - 1];

            if (cnt >= n) {
                r = mid - 1;
            } else {
                l = mid + 1;
            }
        }

        string y = to_string(l);
        int u = y.size();

        long long j = n - ((l - power[u]) * u + digit[u - 1]) - 1;

        return y[j];
    }
};
```

*Generated on: 10/28/2026, 11:52:48 PM*