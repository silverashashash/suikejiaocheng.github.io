## 邻接矩阵

邻接矩阵 Adjacency Matrix

```
[
  [1,0,0,1],
  [0,1,1,0],
  [0,1,1,0],
  [1,0,0,1]
]

```

例如上图表示0号点和3号点有连边。1号点和2号店有连边。  
当然，每个点和自己也是默认有连边的。  
图中的`0`表示不连通，`1`表示连通。  
我们也可以用一个更具体的整数值来表示连边的长度。  
邻接矩阵我们可以直接用一个二维数组表示，如`int[][] matrix;`。这种数据结构因为耗费 O\(n^2\) 的空间，所以在稀疏图上浪费很大，因此并不常用。





