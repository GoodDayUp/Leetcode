---
LeetCode120:三角形最小路径和
---


#### 英文题目：


Given a triangle, find the minimum path sum from top to bottom. Each step you may move to adjacent numbers on the row below.

**For example**, given the following triangle

```
[
        [2],
    [3,4],
    [6,5,7],
    [4,1,8,3]
]
```

The minimum path sum from top to bottom is 11 (i.e., 2 + 3 + 5 + 1 = 11).

**Note:**

Bonus point if you are able to do this using only O(n) extra space, where n is the total number of rows in the triangle.



#### 中文题目：

给定一个三角形，找出自顶向下的最小路径和。每一步只能移动到下一行中相邻的结点上。

**例如**，给定三角形：

```
[
        [2],
    [3,4],
    [6,5,7],
    [4,1,8,3]
]
```

自顶向下的最小路径和为 11（即，2 + 3 + 5 + 1 = 11）。

**说明：**

如果你可以只使用 O(n) 的额外空间（n 为三角形的总行数）来解决这个问题，那么你的算法会很加分。




#### 解答：

##### C++

```
class Solution {
public:
    int minimumTotal(vector<vector<int>>& nums) {
        int n = nums.size();
        vector<vector<long long>> f(n,vector<long long>(n));
        f[0][0] = nums[0][0];
        for (int i=1;i<n;i ++)
            for (int j=0;j<=i;j ++)
            {
                f[i][j]=INT_MAX;
                if (j>0) f[i][j]=min(f[i][j],f[i-1][j-1]+nums[i][j]);
                if (j<i) f[i][j]=min(f[i][j],f[i-1][j]+nums[i][j]);
            }
        long long res = INT_MAX;
        for (int i=0;i<n;i ++) res = min(res,f[n-1][i]);
        return res;
    }
};
```