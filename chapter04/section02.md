# 4.2 朴素贝叶斯法的参数估计

#### 4.2.1 极大似然估计

$$
P(Y = c_k) = \frac{\sum^N_{i=1}I(y_i = c_k)}{N}
$$

$$
P(x^{(j)} = a_{jl} | Y = c_k) = \frac{\sum^N_{i=1} I(x_i^{(j)} = a_{jl}, y_i = c_k)}{\sum^N_{i=1} I(y_i = c_k)}
$$

#### 4.2.2 学习与分类算法

**算法4-1（朴素贝叶斯算法（naive Bayes algorithm））**

输入： 训练数据 $$T = \{(x_1, y_1), (x_2, y_2), \dots, (x_N, y_N)\}$$ ，其中 $$x_i = (x^{(1)}_i, x^{(2)}_i, \dots, x^{(n)}_i)^T$$ ， $$x^{(j)}_i$$ 为第 $$i$$ 个样本的第 $$j$$ 个特征， $$a_{jl}$$ 为第 $$j$$ 个特征的第 $$l$$ 个可能值；实例 $$x$$ 

输出：实例 $$x$$ 的分类

1. 计算先验概率和条件概率：
   1. $$P(Y = c_k) = \frac{\sum^N_{i=1}I(y_i = c_k)}{N} $$
   2. $$P(X^{(j)} = a_{jl} | Y = c_k) = \frac{\sum^N_{i=1}I(X^{(j)} = a_{jl}, y_i = c_k)}{\sum^N_{i=1}I(y_i = c_k)}$$ 
2. 对于给定的实例 $$x$$ ，计算 $$P(Y = c_k) \prod^n_{j=1}P(X^{(j)} = x^{(j)}| Y = c_k)$$ 
3. 确定 $$x$$ 的类 $$y = arg\underset{c_k}{max}P(Y = c_k) \prod^n_{j=1}P(X^{(j)} = x^{(j)}| Y = c_k)$$ 

#### 4.2.3 贝叶斯估计

用极大似然估计可能会出现所需估计的概率值为0的情况。

条件概率的贝叶斯估计

$$
P_{\lambda}(X^{(j)} = a_{jl} | Y = c_k) = \frac{\sum^N_{i=1}I(X^{(j)}_i = a_{jl}, y_i = c_k) + \lambda}{\sum^N_{i=1}I(y_i = c_k) + S_j \lambda}
$$

其中 $$\lambda \geq 0$$ ，当 $$\lambda = 0$$ 时，为极大似然估计；当 $$\lambda = 1$$ 时，为拉香拉斯平滑（Laplace smoothing）。

先验概率的贝叶斯估计

$$
P_{\lambda}(Y = c_k) = \frac{\sum^N_{i=1}I(y_i = c_k) + \lambda}{N + K\lambda}
$$



