---
LeetCode84:柱形图中最大的矩形(Largest Rectangle in Histogram)
---


#### 英文题目：



Given n non-negative integers representing the histogram's bar height where the width of each bar is 1, find the area of largest rectangle in the histogram.

 ![在这里插入图片描述](https://img-blog.csdnimg.cn/20190903182636905.png)


Above is a histogram where width of each bar is 1, given height = [2,1,5,6,2,3].

 ![在这里插入图片描述](https://img-blog.csdnimg.cn/20190903182630420.png)


The largest rectangle is shown in the shaded area, which has area = 10 unit.

 

**Example:**

```
Input: [2,1,5,6,2,3]
Output: 10
```

#### 中文题目：

给定 n 个非负整数，用来表示柱状图中各个柱子的高度。每个柱子彼此相邻，且宽度为 1 。

求在该柱状图中，能够勾勒出来的矩形的最大面积。

 ![在这里插入图片描述](https://img-blog.csdnimg.cn/20190903182341417.png)

以上是柱状图的示例，其中每个柱子的宽度为 1，给定的高度为 [2,1,5,6,2,3]。

 ![在这里插入图片描述](https://img-blog.csdnimg.cn/20190903182350767.png)

图中阴影部分为所能勾勒出的最大矩形面积，其面积为 10 个单位。

 

**示例:**

```
输入: [2,1,5,6,2,3]
输出: 10
```



#### 解答：

##### C++

```
class Solution {
public:
    int largestRectangleArea(vector<int>& heights) {
        int n=heights.size();
        vector<int> left(n),right(n);
        
        stack<int> stk;
        for (int i=0;i<n;i ++)
        {
            while (stk.size() && heights[stk.top()]>=heights[i]) stk.pop();
            if (stk.empty()) left[i]=-1;
            else left[i]=stk.top();
            stk.push(i);
        }
        while (stk.size()) stk.pop();
        for (int i=n-1;i>=0;i --)
        {
            while (stk.size() && heights[stk.top()]>=heights[i]) stk.pop();
            if (stk.empty()) right[i]=n;
            else right[i]=stk.top();
            stk.push(i);
        }
        int res=0;
        for (int i=0;i<n;i ++) res=max(res,heights[i]*(right[i]-left[i]-1));
        return res;
    }
};
```