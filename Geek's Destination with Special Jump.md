## 01. Geek's Destination with Special Jump

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/geek-and-her-destination--145724/1?_gl=1*12c2bk0*_up*MQ..*_gs*MQ..&gclid=Cj0KCQjwlYHBBhD9ARIsALRu09pbgqNAyqVxhcm8IAnjUTMlLJhIC1w5aC7xa3QAQYivF9iTVK4woaUaAsehEALw_wcB&gbraid=0AAAAAC9yBkCuY1XCOe54dwAzS3bpeogBG)

### Problem Description

**Task:** Geek starts at position 0 on the positive X-axis and needs to reach or pass position d on the positive X-axis. Geek normally follows a repeating movement pattern:Move forward by a units, taking a seconds.Move backward by b units, taking b seconds.Geek also has a special jump that moves him exactly j units forward in 1 second. He can use it at any time, even in the middle of a forward or backward movement, and the journey ends immediately after the jump.Given five integers a, b, d, l, and r. For every integer j in the range [l, r], find the minimum time required for Geek to reach or pass position d. He may either use the special jump or reach the destination using normal movement alone, whichever takes less time.Return the sum of the minimum times for all jump lengths from l to r. Since, the answer can be large, return modulo 10⁹ + 7. Note: Each jump length is considered independently.Examples:Input: a = 2, b = 1, d = 5, l = 3, r = 4Output: 5Explanation: For j = 3, Geek moves 2 units forward, then takes a jump of 3 units to reach the destination. The minimum time required is 3 seconds.For j = 4, Geek moves 1 unit forward, then takes a jump of 4 units to reach the destination. The minimum time required is 2 seconds.Total sum for the range [l, r] = 3 + 2 = 5.Input: a = 4, b = 2, d = 8, l = 2, r = 4Output: 26Explanation:For j = 2, Geek moves 4 units forward, then 2 units backward. She then moves 4 units forward again and takes a jump of 2 units to reach the destination. The minimum time required is 11 seconds.For j = 3, Geek moves 4 units forward, then 2 units backward. She then moves 3 units forward and takes a jump of 3 units to reach the destination. The minimum time required is 10 seconds.For j = 4, Geek moves 4 units forward, then takes a jump of 4 units to reach the destination. The minimum time required is 5 seconds.Total sum for the range [l, r] = 11 + 10 + 5 = 26.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(1)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (1)

#### Solution 1 (C++)

- **Submitted:** 2026-11-25 23:34:41
- **Status:** Correct
- **Marks:** 8

```cpp
class Solution {
  public:
    int minTime(int a, int b, int d, int l, int r) {
        const long long MOD = 1000000007LL;
        long long net = a - b;
        auto time_to = [&](long long x) -> long long {
            if (x <= 0) return 0;
            if (x <= a) return x;
            long long m = (x - a + net - 1) / net;
            return x + 2LL * b * m;
        };
        long long T0 = time_to(d);
        long long left = d - (long long)r;
        long long right = d - (long long)l;
        long long threshold = T0 - 1;
        long long lo = 0, hi = d, best = -1;
        while (lo <= hi) {
            long long mid = lo + (hi - lo) / 2;
            if (time_to(mid) <= threshold) {
                best = mid;
                lo = mid + 1;
            } else {
                hi = mid - 1;
            }
        }
        auto sum_ceil_1_to = [&](long long M) -> long long {
            if (M <= 0) return 0;
            long long q = M / net;
            long long rr = M % net;
            return net * q * (q + 1) / 2 + (q + 1) * rr;
        };
        auto sum_f = [&](long long L, long long R) -> long long {
            if (L > R) return 0;
            long long cnt = R - L + 1;
            long long sum_s = cnt * (L + R) / 2;
            long long start_u = std::max(L, (long long)a + 1) - a;
            long long end_u = R - a;
            long long sum_g = 0;
            if (start_u <= end_u) {
                sum_g = sum_ceil_1_to(end_u) - sum_ceil_1_to(start_u - 1);
            }
            return sum_s + 2LL * b * sum_g;
        };
        long long sum = 0;
        if (best >= right) {
            sum = (right - left + 1) + sum_f(left, right);
        } else if (best < left) {
            sum = (right - left + 1) * T0;
        } else {
            long long cnt_jump = best - left + 1;
            long long cnt_t0 = right - best;
            sum = cnt_jump + sum_f(left, best) + cnt_t0 * T0;
        }
        return (int)(sum % MOD);
    }
};
```

*Generated on: 11/25/2026, 11:35:07 PM*