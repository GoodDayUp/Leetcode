---
LeetCode53:最大子序和(Maximum Subarray)
---

#### 英文题目：



Given an integer array nums, find the contiguous subarray (containing at least one number) which has the largest sum and return its sum.




**Example:**

```
Input: [-2,1,-3,4,-1,2,1,-5,4], 
Output: 6 
Explanation: [4,-1,2,1] has the largest sum = 6.
```


#### 中文题目：
给定一个整数数组 nums ，找到一个具有最大和的连续子数组（子数组最少包含一个元素），返回其最大和。



**示例:**

```
输入: [-2,1,-3,4,-1,2,1,-5,4],
输出: 6
解释: 连续子数组 [4,-1,2,1] 的和最大，为 6。
```

**进阶:**

如果你已经实现复杂度为 O(n) 的解法，尝试使用更为精妙的分治法求解。



#### 解答：

##### C++

```
class Solution {
public:
    int maxSubArray(vector<int>& nums) {
        int res = INT_MIN, last = 0;
        for (int i=0;i<nums.size();i ++ )
        {
            int now = max(last,0)+nums[i];
            res = max(res,now);
            last = now;
        }
        return res;
    }
};
```