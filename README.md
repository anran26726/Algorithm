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

 
注意事项： 

开闭区间，缩小时候是否+1/-1 （考虑当前的mid是否可能会是你potential的解） 

取中间值时，mid是否会和left和right重复 

循环条件，即手里left和right的关系 

 

 

两种题目类型： 

常规二分 

答案二分 

在可能的答案的解集空间上进行二分 
