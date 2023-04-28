# Leecode 学习笔记

## 线性表

### 题号1 两数之和

- 题目描述

  给定一个整数数组 nums 和一个整数目标值 target，请你在该数组中找出 和为目标值 target  的那 两个 整数，并返回它们的数组下标。

  你可以假设每种输入只会对应一个答案。但是，数组中同一个元素在答案里不能重复出现。

  你可以按任意顺序返回答案

  - 示例

    输入：nums = [2,7,11,15], target = 9
    输出：[0,1]
    解释：因为 nums[0] + nums[1] == 9 ，返回 [0, 1] 。

- 解题思路

  - 老思路

    - 最开始想到采用暴力算法设置两个游标i，j对每一个元素都和其后的所有元素作比较，这样显然没问题，但时间复杂度达到O($n^2$)，时间复杂度过高

  - 新思路

    - 先对数组进行快速排序
    - 对排序好的数组设置头尾指针low和high，向中间遍历，比较两数之和
    - 如果小于目标值则low++，反之high--
    - 直到找到目标或者一边循环结束跳出循环

  - 新思路时间复杂度变为：O(nlogn)(排序）+O(n)（查找）=O(nlogn)

    >
    >
    >但是对于快排来说时间复杂度在基本乱序的时候才是nlogn，在与目标序列逆序的时候退化为冒泡排序时间复杂度变为$n^2 $所以可以采用归并或者堆排序就一定是nlogn

- 遇到的问题

  - 由于数组首先经过排序导致下标变化，题目需要返回原始下标

    ```java
    int []a=nums
    ```

    - 由于这样直接使用a数组记录原始序列，两者会指向堆空间的同一地址区域，所以压根就没能保存原数组的序列，即我们需要在堆中单独声明一个数组

    ```java
    int[] a=new int[]{};
    a=nums.clone();
    ```

  - 对于Array类中的sort快排参数是0和数组长度，其在内部实现了下标的转化

- 代码示例

  ```java
  package twoSum;
  
  import java.util.Arrays;
  
  public class Solution {
      public int[] twoSum(int[] nums, int target) {
          /**
           * 设置a数组的目的就是为了保存原数组的序列
           * 如果像下面这样，两者会指向堆空间的同一地址区域
           * 所以压根就没能保存原数组的序列
           * 即我们需要在堆中单独声明一个数组
           */
          //int []a=nums;
          int[] a=new int[]{};
          a=nums.clone();
          Arrays.sort(nums,0,nums.length);
          //int result[]=new int[]{-1,-1};
          Boolean flag1=false;
          Boolean flag2=false;
          int [] result=new int[2];
          int low=0;
          int high=nums.length-1;
          while(low<high){
              if(nums[low]+nums[high]<target){
                  low++;
  
              }else if(nums[low]+nums[high]>target){
                  high--;
              }else{
                  for(int i=0;i<nums.length;i++){
                      if(a[i]==nums[low]||a[i]==nums[high]){
                          if(flag1==false){
                              result[0]=i;
                              flag1=true;
  //                            System.out.println(a[i]);
                          }else{
                              result[1]=i;
                              flag2=true;
  //                            System.out.println(a[i]);
                          }
                      }
                      if(flag2==true){
                          break;
                      }
                  }
                  break;
              }
          }
          return result;
      }
  }
  ```

## 字符串

### 题号3  无重复的最长子串

- 题目描述

  - 给定一个字符串 `s` ，请你找出其中不含有重复字符的 **最长子串** 的长度。

  - 示例

    输入: s = "abcabcbb"
    输出: 3 
    解释: 因为无重复字符的最长子串是 "abc"，所以其长度为 3

- 解题思路

  - 暴力算法：时间复杂度O($n^3$)

    - 基本步骤

      - 设置两个游标i，j
      - i用于遍历整个字符串
      - j用于判断i后的子串中是否出现有与i相同的字符
      - 若有则返回最大长度，并使i向后移动继续遍历

    - 遇到的问题

      - leecode报错但本地不报错

        ![image-20230323190704812](C:\Users\31783\AppData\Roaming\Typora\typora-user-images\image-20230323190704812.png)

        其原因是本地的类名和leecode中的默认类名不相同导致

      -  HashSet

        - 在泛型中需要的是类名，也就是说当其是基本数据类型时，得用其包装类

        ```java
        HashSet<Character> hashSet=new HashSet<>();
        //而不能是下式
        //HashSet<char> hashSet=new HashSet<>();
        ```

        

    - 缺点：

      - 由于时间复杂度是$n^3$太高了，数据量很大的时候往往会超时，极力不推荐

  - 滑动窗口算法：常常用于字符串中提升性能，减少for的嵌套

    - 基本步骤

      - 设置两个游标left和right从0开始
      - 每次判断right对应的字符是否在hashset中
      - 如果不在则将其添加，并使right++
      - 如果在则将left对应的字符从hashset中删除，并使left++（两个字符发生了重复）
      - 一直迭代到right移动至字符串末尾

    - 时间复杂度：O($n$)

    - 缺点

      - 由于判断该字符是否在hashset中相当于会遍历hashset所以效率不算最好，改进方法见ASCII映射法

    - 代码示例

      ```java
      package LongestSubstring;
      
      import java.util.HashSet;
      
      class Solution {
      
          public int lengthOfLongestSubstring(String s) {
              final int len=s.length();
              int left=0;
              int right=0;
              int maxSize=0;
              HashSet<Character> hashSet=new HashSet<>();
              while(right<len){
                  if(!hashSet.contains(s.charAt(right))){
                      hashSet.add(s.charAt(right));
                      right++;
                      maxSize=Math.max(maxSize,right-left);
                  }else{
                      hashSet.remove(s.charAt(left));
                      left++;
                  }
              }
              return maxSize;
          }
      }
      ```

  - ASCII映射法（也就是滑动窗口的改进版）

    - 基本步骤

      - 建立一个128长度的数组记录每个字符串最后一次出现的位置
      - 设置一个两个游标left和right
      - right向遍历整个字符串，每次都查询该字符是否在之前出现过，如果出现过则比较right-left+1的值（也就是子串长度）和记录字串长度的res进行大小比较
      - 如果right对应的字符已经出现过，判断其出现的位置如果在left之后则改变left的值为该字符上一次出现的位置（模拟窗口的滑动）

    - 优点：

      - 由于数组是随机存取的，在存取的时候时间复杂度是O(1)，则会大大优化滑动窗口法对于判断该字符是否出现在hashset中的遍历O(n)所需的时间复杂度

    - 代码示例

      ```java
      
      class Solution2 {
              public int lengthOfLongestSubstring(String s) {
                  // 记录字符上一次出现的位置
                  int[] last = new int[128];
                  for (int i = 0; i < 128; i++) {
                      last[i] = -1;
                  }
                  int len = s.length();
                  int res = 0;
                  int left = 0;
                  for (int right = 0; right < len; right++) {
                      int index = s.charAt(right);
                      left = Math.max(left, last[index] + 1);
                      res = Math.max(res, right - left  + 1);
                  }
                  return res;
              }
      }
      ```

  ### 题号49 