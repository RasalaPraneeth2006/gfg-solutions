## 01. Minimum Squares with Full Cuts

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/squares-in-reactangle3340/1?_gl=1*orq810*_up*MQ..*_gs*MQ..&gclid=Cj0KCQjwlYHBBhD9ARIsALRu09pbgqNAyqVxhcm8IAnjUTMlLJhIC1w5aC7xa3QAQYivF9iTVK4woaUaAsehEALw_wcB&gbraid=0AAAAAC9yBkCuY1XCOe54dwAzS3bpeogBG)

### Problem Description

**Task:** Given a rectangular paper with dimensions n × m, find the minimum number of squares that can be formed by cutting the paper. Each cut must be made completely across the remaining paper, either horizontally or vertically.Examples:Input: n = 4, m = 5

#### Examples

##### Example 1

- **Output:**
```text
8
```
- **Explanation:** One square of size 11 x 11, five squares of size 2 x 2, and two squares of size 1 x 1 are formed by following the rule. Please note that if we are allowed to make partial horizontal or vertical cuts, we can have 6 squares which is a different interesting problem, Min Cut Square.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(log(min(n, m)))
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (3)

#### Solution 1 (Java)

- **Submitted:** 2026-10-12 09:47:03
- **Status:** Correct
- **Marks:** 0

```java
class Solution {
    public int minSquares(int n, int m) {
        // code here
        if(n == 0)return 0;
        return m / n + minSquares(m%n, n);
    }
}
```

#### Solution 2 (Java)

- **Submitted:** 2026-10-12 09:45:26
- **Status:** Correct
- **Marks:** 0

```java
class Solution {
  public:
    int minSquares(int n, int m) {
        // code here
        if(n == 0)return 0;
        return m / n + minSquares(m%n, n);
    }
};
```

#### Solution 3 (Java)

- **Submitted:** 2026-10-12 09:37:04
- **Status:** Correct
- **Marks:** 4

```java
class Solution {
  public:
    int minSquares(int n, int m) {
        // code here
        if(n == 0)return 0;
        return m / n + minSquares(m%n, n);
    }
};
```

*Generated on: 10/12/2026, 9:49:43 AM*