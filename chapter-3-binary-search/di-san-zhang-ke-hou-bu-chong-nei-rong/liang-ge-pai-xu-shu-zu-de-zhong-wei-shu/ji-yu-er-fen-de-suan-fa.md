## 基于二分的算法

问题描述

求两个排好序的数组合并在一起之后，他们最中间的那个数是谁。如果总共有偶数个数，那么返回中间的两个数的平均值。

LintCode 练习地址：[http://www.lintcode.com/problem/median-of-two-sorted-arrays/](http://www.lintcode.com/problem/median-of-two-sorted-arrays/)

#### 算法描述

1. 我们需要先确定二分的上下界限，由于两个数组**A, B**均有序，所以下界为`min(A[0], B[0])`，上界为`max(A[A.length - 1], B[B.length - 1])`.
2. 判断当前上下界限下的`mid(mid = (start + end) / 2)`是否为我们需要的答案；这里我们可以分别对两个数组进行二分来找到两个数组中小于等于当前`mid`的数的个数`cnt1`与`cnt2`，`sum = cnt1 + cnt2`即为`A`跟`B`合并后小于等于当前mid的数的个数.
3. 如果`sum<k`，即中位数肯定不是`mid`，应该大于`mid`，更新`start`为`mid`，否则更新`end`为`mid`，之后再重复第二步
4. 当不满足`start + 1<end`这个条件退出二分循环时，再分别判断一下`start`跟`end`，最终返回符合要求的那个数即可

#### 算法详解

如果对该算法有点疑问，我们下面来详细讲解一下：

* 这一题如果用二分法来做，其实就是一个二分答案的过程
* 首先我们已经得到了上下界限，那么答案必定是在这个上下界限中的，需要实现的就是从这个歌上下界限中找出答案
* 我们每次取的`mid`，其实就是我们每次在假设答案为`mid`，二分的过程就是不断的推翻这个假设，然后再假设新的答案
* 需要满足的条件为：
  * 上面算法描述中的`sum`需要等于`k`，这里的`k = (A.length + B.length) / 2`. 如果`sum<k`，很明显当前的`mid`偏小，需要增大，否则就说明当前的`mid`偏大，需要缩小.
* 最终在`start`与`end`相邻的时候退出循环，判断`start`跟`end`哪个符合条件即可得到最终结果 


