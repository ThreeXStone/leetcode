### 区间合并
**问题描述**：合并所有重叠的区间，并返回一个不重叠的区间数组

#### 方法思路
1. **排序区间**：首先将区间按照起始点进行排序，这样我们可以按顺序处理区间，更容易合并重叠的区间。
2. 初始化一个空列表来存储合并后的区间。遍历排序后的区间列表，如果当前区间与结果列表中的最后一个区间重叠，则合并它们（更新最后一个区间的结束点为两者结束点的最大值）；否则，将当前区间添加到结果列表中。

```python
class Solution:
    def merge(self, intervals: List[List[int]]) -> List[List[int]]:
        if not intervals:
            return []
        #key参数允许我们指定一个函数，这个函数会应用于列表中的每个元素，然后根据函数的返回值进行排序。
        #lambda 关键字表示定义一个匿名函数
        #x 是函数的参数（这里代表列表中的每个元素）,x[0] 是函数的返回值（这里返回每个子列表的第一个元素）
        intervals.sort(key=lambda x: x[0])
        merged = []
        
        for interval in intervals:
            if not merged or merged[-1][1] < interval[0]:
                merged.append(interval)
            else:
                merged[-1][1] = max(merged[-1][1], interval[1])
        
        return merged
```

**相关题目：** 56
