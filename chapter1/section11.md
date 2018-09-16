# 1.11 习题

#### 1.11.1 

**学习方法的三要素：**模型，策略，算法。

**伯努利模型：** $$P(A) = \left\{\begin{matrix}\theta & A = 1\\ 1 - \theta & A = 0\end{matrix}\right.$$ 

**极大似然估计：**

$$
L(\theta) = \Pi_{i=1}^n P(A_i) = \theta^k(1-\theta)^{n-k} \\
\Rightarrow L'(\theta) = k\theta^{k-1}(1-\theta)^{n-k} + (k-n)\theta^k(1-\theta)^{n-k-1}
$$

令 $$L'(\theta) = 0 $$ ：

$$
k(1-\theta) + (k-n)\theta = 0 \Rightarrow \theta = \frac{k}{n}
$$

**贝叶斯估计：**

