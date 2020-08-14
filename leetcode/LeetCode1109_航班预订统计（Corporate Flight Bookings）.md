---
LeetCode1109:航班预定统计(Corporate Flight Bookings)
---


#### 英文题目：


There are n flights, and they are labeled from 1 to n.

We have a list of flight bookings.  The i-th booking bookings[i] = [i, j, k] means that we booked k seats from flights labeled i to j inclusive.

Return an array answer of length n, representing the number of seats booked on each flight in order of their label.






**Example:**
```
Input: bookings = [[1,2,10],[2,3,20],[2,5,25]], n = 5
Output: [10,55,45,25,25]
```

**Constraints:**
```
1 <= bookings.length <= 20000
1 <= bookings[i][0] <= bookings[i][1] <= n <= 20000
1 <= bookings[i][2] <= 10000
```

#### 题解：

暴力枚举O（n+m）
1.根据题目，给定一个全为0的数组，然后每次将区间 [i, j] 统一增加k，问操作了若干次之后每个位置的值为多少

2.转换为使用端点，例如[i, j] 我们可以在i处增加k， 在j + 1处减少k，
统计时，记res[i] = res[i] + res [i-1]

时间复杂度：
每个区间遍历一次，每个位置遍历一次，股时间复杂度为O（m+n），其中n为位置的个数，m为区间的个数。

空间复杂度：
O（n）


#### 中文题目：
这里有 n 个航班，它们分别从 1 到 n 进行编号。

我们这儿有一份航班预订表，表中第 i 条预订记录 bookings[i] = [i, j, k] 意味着我们在从 i 到 j 的每个航班上预订了 k 个座位。

请你返回一个长度为 n 的数组 answer，按航班编号顺序返回每个航班上预订的座位数。




**示例:**
```
输入：bookings = [[1,2,10],[2,3,20],[2,5,25]], n = 5
输出：[10,55,45,25,25]
```

**提示:**

```
1 <= bookings.length <= 20000
1 <= bookings[i][0] <= bookings[i][1] <= n <= 20000
1 <= bookings[i][2] <= 10000
```

#### 解答：

##### Python3
```
class Solution:
    def corpFlightBookings(self, bookings: List[List[int]], n: int) -> List[int]:
        res = [0] * n
        for l, r, seat in bookings:
            res[l - 1] += seat
            if r < n:
                res[r] -= seat
        for i in range(1, n):
            res[i] += res[i-1]
        return res
    
```

