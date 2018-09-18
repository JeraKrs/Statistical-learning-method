# 1.11 习题

#### 1.11.1 

**学习方法的三要素：**模型，策略，算法。

**伯努利模型：** $$P(A | \theta) = \left\{\begin{matrix}\theta & A = 1\\ 1 - \theta & A = 0\end{matrix}\right.$$ 

**极大似然估计：**

$$
L(\theta) = \Pi_{i=1}^n P(A_i | \theta) = \theta^k(1-\theta)^{n-k} \\
\Rightarrow L'(\theta) = k\theta^{k-1}(1-\theta)^{n-k} + (k-n)\theta^k(1-\theta)^{n-k-1}
$$

令 $$L'(\theta) = 0 $$ ：

$$
k(1-\theta) + (k-n)\theta = 0 \Rightarrow \theta = \frac{k}{n} \\
\theta = arg\underset{\theta}{max}L(\theta) = \frac{k}{n}
$$

**贝叶斯估计：**

$$
L(\theta) = P(\theta | A) = \frac{P(A | \theta) P(\theta)}{P(A)}
$$

因为 $$P(A | \theta)$$ 服从伯努利分布，所以假设 $$P(\theta)$$ 服从 $$\beta$$ 分布（共轭分布），并且 $$P(A)$$ 是固定的，所以只需要考虑 $$L(\theta)$$ 中的分子。

$$
L(\theta) = \Pi^n_{i=1}P(A_i | \theta) \times P(\theta) \\
= \theta^k(1-\theta)^{n-k}\theta^{a-1}(1-\theta)^{b-1} \\
= \theta^{k+a-1}(1-\theta)^{n+b-k-1} \\
\Rightarrow L'(\theta) = (k + a - 1)\theta^{k+a-2}(1-\theta)^{n+b-k-1} - (n + b - k - 1)\theta^{n + a - 1}(1-\theta)^{n+b-k-2}
$$

令 $$L'(\theta) = 0$$ ：

$$
(k + a - 1)(1 - \theta) - (n + b - k - 1)\theta = 0 \\
\Rightarrow (n + a + b - 2)\theta = k + a - 1 \\
\Rightarrow \theta = \frac{k + a - 1}{n + a + b - 2} \\
\theta = arg\underset{\theta}{max} \frac{k + a - 1}{n + a + b - 2}
$$

其中， $$P(\theta)$$ 的超参数 $$a, b$$ 初始值选择直接影响模型的收敛速度。

**1.11.2**

经验风险（使用对数损失函数）： $$L(\theta) = \frac{1}{n}\Pi^{n}_{i=1}-\log P(y_i | x_i)$$ 

$$
L(\theta) = -\frac{1}{n} \log P(Y | X) \\
\Rightarrow arg\underset{\theta}{min} L(\theta) = arg\underset{\theta}{max}P(Y | X)
$$



