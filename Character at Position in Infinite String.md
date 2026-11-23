## 01. Character at Position in Infinite String

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/the-infinite-string1049/1?_gl=1*vh7006*_up*MQ..*_gs*MQ..&gclid=Cj0KCQjwlYHBBhD9ARIsALRu09pbgqNAyqVxhcm8IAnjUTMlLJhIC1w5aC7xa3QAQYivF9iTVK4woaUaAsehEALw_wcB&gbraid=0AAAAAC9yBkCuY1XCOe54dwAzS3bpeogBG)

### Problem Description

**Task:** Given a string s and an integer pos, an infinite string is constructed by repeatedly applying the following operation. In the i-th step, append i consecutive $ characters, followed by the reverse of the current string, to the current string.Formally, if the current string is s, update it as:s = s + ('$' repeated i times) + reverse(s)The initial string is the given s, and the process continues indefinitely. Find and return the character at the pos(1-based indexing) in the resulting infinite string.Examples:Input: s = "12345", pos = 3

#### Examples

##### Example 1

- **Output:**
```text
3
```
- **Explanation:** In "12345...", the character at pos 3 is 3.

##### Example 2

- **Input:**
```text
s = "12345", pos = 10
```
- **Output:**
```text
2
```
- **Explanation:** In "12345$54321...", the character at pos 10 is 2.

##### Example 3

- **Input:**
```text
s = "abc", pos = 7
```
- **Output:**
```text
a
```
- **Explanation:** In "abc$cba...", the character at pos 7 is a.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(log (pos))
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (1)

#### Solution 1 (C++)

- **Submitted:** 2026-11-23 12:16:37
- **Status:** Correct
- **Marks:** 4

```cpp
class Solution {
  public:
    char posInfinite(string &s, int pos) {
        long long p = pos;
        long long len = s.size();
        int steps = 0;
        while (len < p) {
            steps++;
            len = 2 * len + steps;
        }
        long long cur_len = len;
        int cur_step = steps;
        while (cur_step > 0) {
            long long prev_len = (cur_len - cur_step) / 2;
            if (p <= prev_len) {
                cur_len = prev_len;
                cur_step--;
            } else if (p <= prev_len + cur_step) {
                return '$';
            } else {
                long long offset = p - prev_len - cur_step;
                p = prev_len - offset + 1;
                cur_len = prev_len;
                cur_step--;
            }
        }
        return s[p - 1];
    }
};
```

*Generated on: 11/23/2026, 12:17:00 PM*