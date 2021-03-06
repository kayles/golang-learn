# 1. Add Sum

## Problem

### Description

Given an array with n integers, your task is to check if it could become non-decreasing by modifying at most 1 element.

We define an array is non-decreasing if array[i] <= array[i + 1] holds for every i (1 <= i < n).
### Example
```cpp
Input: [4,2,3]
Output: True
Explanation: You could modify the first 4 to 1 to get a non-decreasing array.

Input: [4,2,1]
Output: False
Explanation: You can't get a non-decreasing array by modify at most one element.
```
> Note: 如果array [i] <= array [i + 1]对于每个i（1 <= i <n）成立，我们定义一个数组是非递减的。

>优先把 nums[i]降为nums[i+1]，这样可以减少 nums[i+1] > nums[i+2] 的风险。

## Solution
### Approach1
在遍历数组时用 Stack 把数组中的数存起来，如果当前遍历的数比栈顶元素来的大，说明栈顶元素的下一个比它大的数就是当前元素。

### Approach2
> 通过交换对0,1,2进行排序复杂度 O(n)
```go
i=0, j=n,循环k保证循环不变式

[0...i-1]   是0
[i...k-1]   是1
[k,j-1]     是未探测
[j,n-1]     是2
初始k=0时0,1,2所有区域是空,归纳证明任然满足上述条件，循环k=0 to j-1

若 a[k] == 0 swap(a[i++],a[k])
若 a[k] == 1 无操作
若 a[k] == 2 swap(a[--j],a[k--])
复杂度分析O(n),对于k要么k++，要么j--
```
```go
2 0 2 1 1 0
0 0 1 1 2 2

START
2 0 2 1 1 0   i=0 k=0 j=6
0 0 2 1 1 2   i=0 k=0 j=5
0 0 2 1 1 2   i=1 k=1 j=5
0 0 2 1 1 2   i=2 k=2 j=5
0 0 1 1 2 2   i=2 k=2 j=4 
0 0 1 1 2 2   i=2 k=3 j=4
0 0 1 1 2 2   i=2 k=4 j=4
END
```
