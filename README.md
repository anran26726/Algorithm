# Algorithm
整理一些算法相关知识点和题目
# 二分法
Clarify Questions: 
  数据类型 
  input的数据结构类型 
  返回值的类型：是值还是index / 是boolean还是数据本身 
  数据特征: Array是否sorted / 是否有重复 / 数据边界 / 大小范围 
Implementation: 
  输入检查 
  代码风格 
  Test:
    实现部分的正确性 
    output是我们想要的 (想要变的部分和我们所期望的一样) 
    不应该变的部分 不应该被改变 
    数据的完整性 
    Corner case (error handling) 

Binary Search: 
  1句总结: 什么是Binary Search 
    一种在有序区间(*) 内通过按比例缩小范围(/2)来达到O(lgn)时间复杂度的搜索方式 
    n个数 每次/2 -> 进行了x次找到最终结果(1) 
    2^x = n 
    x = lgn 
  2个原则： 
    确保缩小区间 
    确保没有丢解 
  3种情况： 
    针对查找精确解 (可以handle找不到的情况的):
      给定一个sorted array，int target, 需要找到index -> array[index] = target 
      while (l <= r) { // 退出条件, l = r + 1 
        int mid = l + (r - l) / 2; // mid -> [l, r] 
        if (array[mid] == target) 
          return mid; 
        else if (array[mid] > target) 
          r = mid - 1; // [left, mid) 
        else 
          l = mid + 1; 
    } 

 

针对查找模糊解： 

给定一个sorted array(有重复)，int target, 需要找到target第一次出现的index (first occurance) 

[0, 1, 2, 2, 3, 3, 4, 5] 

while (l < r) { // 退出条件，l == r 

int mid = l + (r - l) / 2; // mid -> [l, r) 

If (array[mid] == target) 

r = mid; // [left, mid] 

else if (array[mid] > target) 

r = mid - 1; // [left, mid) 

else // array[mid] < target 

l = mid + 1; // (mid, right] 

} 
return l; 

给定一个sorted array (有重复)， int target。 需要找到target最后一次出现的index (last occurance) 

while (l < r) { // 退出条件，l == r 

int mid = l + (r - l + 1) / 2; // mid -> (l, r] //只有当我们l和r差1的时候才会发生 

If (array[mid] == target) 

l = mid; // [left, mid] 

else if (array[mid] > target) 

r = mid - 1; // [left, mid) 

else // array[mid] < target 

l = mid + 1; // (mid, right] 

} 

return l; 

 

[1, 2] target = 1 -> mid  = 0, left = 0, right = 1 

 

给定sorted array(有重复) int target, 需要找到比target大的第一次出现的index (first occurrence) 

while (l < r) { // 退出条件，l == r 

int mid = l + (r - l) / 2; // mid -> [l, r) 

if (array[mid] == target) 

l = mid + 1; 

else if (array[mid] > target) 

r = mid;  

else // array[mid] < target 

l = mid + 1; 

} 

return l; 

 

万用型：// 思路铺垫：所有痛苦的根源都是因为我们mid的取值可能有闭区间，也就是说mid可能等于left 或者 right的其中一个 

// 因为mid可能与left/right重合，所以我们在做left = mid or right = mid时要格外小心 

—> 那我们能不能让mid和left与right永远不相等呢 -> 保证我们手里至少有3个数 (left + 1 < right) 

 

while (l + 1 < r) { // 退出条件，l + 1 = r 

Int mid = l + (r - l) / 2; // mid -> (l, r) 

If (array[mid] == target) 

// 看情况 

else If (array[mid] > target) 

r = mid; 

else 

l = mid; 

} 

 

// 额外的判断检查！因为退出之后，你手里有两个不同的数 

return array[left] == target? Left : right; // assume first occurance  

 

 

注意事项： 

开闭区间，缩小时候是否+1/-1 （考虑当前的mid是否可能会是你potential的解） 

取中间值时，mid是否会和left和right重复 

循环条件，即手里left和right的关系 

 

 

两种题目类型： 

常规二分 

答案二分 

在可能的答案的解集空间上进行二分 

 

 

Add-on: 

 

Find the closest element with the target (find element i that has the smallest abs(target-nums[i])) 
