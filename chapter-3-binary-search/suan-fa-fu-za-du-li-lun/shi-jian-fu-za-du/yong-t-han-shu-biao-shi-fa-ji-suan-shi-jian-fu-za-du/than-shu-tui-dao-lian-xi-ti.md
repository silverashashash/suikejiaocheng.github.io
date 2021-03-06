## T函数推导练习题

### 练习题 1

有一个算法大致结构如下：

```
while (n >1) {
   这里执行一个使用 O(n) 的算法，将 n 的规模缩小一半
   n = n / 2
}

```

问该算法的时间复杂度?

根据算法，我们可以用`T函数推导法`写出公式：T\(n\) = T\(n/2\) + O\(n\)

推导过程如下：

```
T(n) = T(n/2) + O(n)
     = T(n/4) + O(n/2) + O(n)
     = T(n/8) + O(n/4) + O(n/2) + O(n)
     = ...
     = O(1) + O(2) + ... O(n/2) + O(n)
     = O(1 + 2 + 4 .. + n/2 + n)
     = O(2n) = O(n)

```

许多同学会拍脑袋认为这个式子的结果是 O\(nlogn\)，这是错误的。主要错在，当 T\(n/2\) 往下继续展开的时候，很多同学直接写成 T\(n/4\) + O\(n\)，这是不对的。应该是 T\(n/4\) + O\(n/2\)。这里我们暂时不能约掉 O\(n/2\) 里的`/2`。因为会导致误差累积。

另外一个需要记住的结论就是：`O(1 + 2 + 4 ... + n/2 + n) = O(n)`。这个结论可以通过简单的将 n = 1024 带入计算可以得到：

```
1 + 2 + 4 + ... + 1024 = 2047 ~ 2 * 1024 = O(2n) = O(n)

```

这是一道小学数学题，给整个式子 + 1，然后两个1就变成了一个2，两个2就变成了一个4，以此类推。



### 练习题 2

请用 T 函数来推导归并排序算法的时间复杂度

  
归并排序算法的步骤为：

1. 找出数组的中点
2. 将数组分成两个部分递归执行该算法，分别排序两个部分
3. 合并两个排序好的子数组到一个大数组

写成T函数为：T\(n\) = 2\*T\(n/2\) + O\(n\)，其中

* 2\*T\(n/2\)代表将 n 的问题，拆分为两个 n/2 的同类问题去进行处理。
* O\(n\)代表了，合并两个排好序的 n/2 大小的数组的时间复杂度。

我们用展开的方式推导该算法下的 T\(n\):

```
T(n) = 2 * T(n/2) + O(n)
     = 2 * (2 * T(n/4) + O(n/2)) + O(n)
     = 4 * T(n/4) + 2 * O(n/2) + O(n)
     = 4 * T(n/4) + 2 * O(n)
     = 4 * (2 * T(n/8) + O(n/4)) + 2 * O(n)
     = 8 * T(n/8) + 3 * O(n)
     = 16 * T(n/16) + 4 * O(n)
     ...
     = n * T(1) + logn * O(n)
     = O(n) + O(nlogn)
     = O(nlogn)

```

  
练习题 3

如果一个算法，每次通过 O\(1\) 的时间将 n 的问题拆分为两个 n/2 的问题，求时间复杂度。

首先写出推导函数：T\(n\) = 2 \* T\(n/2\) + O\(1\)，然后进行推导：

```
T(n) = 2 * T(n/2) + O(1)
     = 2 * (2 * T(n/4) + O(1)) + O(1)
     = 4 * T(n/4) + O(2 + 1)
     = 8 * T(n/8) + O(4 + 2 + 1)
     ...
     = n * T(1) + O(n/2 + n/4 + ... + 2 + 1)
     = O(n) + O(n)
     = O(n)

```

这里 O\(n/2 + n/4 + ... 2 + 1\) = O\(n\) 的推导和练习 1 一样。  


