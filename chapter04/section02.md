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

