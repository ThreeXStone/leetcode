## 算法步骤
1. **初始化指针**：设置两个指针 `left` 和 `right`，分别指向数组的起始和结束位置
2. **二分查找循环**：
   - 计算中间位置 `mid`
   - 比较中间元素与目标值：
     - 如果相等，直接返回中间位置
     - 如果中间元素小于目标值，调整左指针到 `mid + 1`
     - 如果中间元素大于目标值，调整右指针到 `mid - 1`
3. **确定插入位置**：如果循环结束仍未找到目标值，左指针的位置即为目标值应插入的位置

```python
left, right = 0, len(nums) - 1
while left <= right:
    mid = (left + right) // 2
    if nums[mid] == target:
        return mid
    elif nums[mid] < target:
        left = mid + 1
    else:
        right = mid - 1
return left   #此时left指向target应该插入的位置
```

**参考题目：**  1991
