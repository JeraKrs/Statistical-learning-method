# 3.1 k近邻法

k近邻法（k-nearest neighbour, KNN）是一种基本分类与回归方法。

**算法3-1 （k近邻法）**

输入： $$T = \{ (x_1, y_1), (x_2, y_2), \dots, (x_n, y_n)\}$$ ，其中 $$x_i \in \mathcal{X} = R^n, y_i \in \mathcal{Y} = \{c_1, c_2, \dots, c_k\}$$ ；实例 $$x$$ 。

输出：实例 $$x$$ 所属的类别 $$y$$ 。

1. 根据给定的距离度量，找出距离 $$x$$ 最近的 $$k$$ 个点，覆盖这 $$k$$ 个点的区域记作 $$N_k(x)$$ 
2. 在 $$N_k(x)$$ 中根据分类规则确定 $$x$$ 的所属类别 $$y$$ 

$$
y = arg\underset{c_j}{max} \sum_{x_i \in N_k(x)} I(y_i = c_j)
$$

其中 $$I$$ 为指示函数，当 $$y_i = c_j$$ 时为1，否则为0。





