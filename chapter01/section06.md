# 1.6 泛化能力

#### 1.6.1 泛化误差

学习方法的**泛化能力（generalization ability）**是指该方法学习到的模型对位置数据的预测能力。 

**泛化误差（generalization error）**的定义是学到的模型对于未知数据预测的误差。泛化误差反应了学习方法的泛化能力。

$$
R_{exp}(\hat{f}) = E_{P} [ L(Y, \hat{f}(X))] = \int_{\mathcal{X}\times\mathcal{Y}} L (y, \hat{f}(x))p(x, y)dxdy
$$

#### 1.6.2 泛化误差上界

泛化能力的分析是通过研究泛化误差的概率上界来进行的，即**泛化误差上界（generalization error bound）**。具体来说就是通过比较两种学习方法的泛化误差上界的大小来比较它们的优劣。

泛化误差上界通常具有的性质有：

* 它是样本容量的函数，当样本容量增加时，泛化上界趋于0；
* 它是假设空间容量的函数，假设空间容量越大，模型就越难学，泛化误差上界就越大；

 例：考虑二类分类问题，已知训练数据集 $$T = \{ (x_1, y_1), (x_2, y_2), \dots, (x_N, y_N)\}$$ ，它是从联合概率分布 $$P(X, Y)$$ 独立同分布产生的， $$x \in R^n, y \in \{-1, +1\}$$ 。假设空间是函数的有限集合 $$\mathcal{F} = \{f_1, f_2, \dots, f_d\}$$ ，其中 $$d$$ 是函数个数。设 $$f$$ 是从 $$\mathcal{F}$$ 中选取的函数，那么关于 $$f$$ 的期望风险和经验风险分别是：

$$
R(f) = E[L(Y, f(X))] \\
\hat{R}(f) = \frac{1}{N} \sum^N_{i=1}L(y_i, f(x_i))
$$

经验风险最小化函数是 $$f_N = arg\underset{f \in \mathcal{F}}{min} \hat{R}(f)$$ ，而 $$f_N$$ 的泛化能力为 $$R(f_N) = E[L(Y, f_N(X))]$$ 。

**定理-1.1（泛化误差上界）**

对二类分类，当假定空间 ****$$\mathcal{F}\{f_1, f_2, \dots, f_d\}$$，对任意一个函数 ****$$f \in \mathcal{F}$$ ****至少以概率 $$1 - \delta $$ ****以下不等式成立。

$$
R(f) \leq \hat{R}(f) + \varepsilon (d, N, \delta)
$$

其中 $$\varepsilon (d, N, \delta) = \sqrt{\frac{1}{2N}(\log d + \log \frac{1}{\delta})}$$ 。

