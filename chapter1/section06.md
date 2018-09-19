# 1.6 泛化能力

#### 1.6.1 泛化误差

泛化能力（generalization ability）指学习方法得到的模型对未知数据的预测能力。

泛化误差（generalization error）指期望风险。

$$
R_{exp}(\hat{f}) = E_{P} [ L(Y, \hat{f}(X))] = \int_{\mathcal{X}\times\mathcal{Y}} L (y, \hat{f}(x))p(x, y)dxdy
$$

#### 1.6.3 泛化误差上界

泛化能力的分析是通过研究泛化误差的概率上界来进行的，即泛化误差上界（generalization error bound）

**定理-1.1（泛化误差上界）**

对二类分类，当假定空间 ****$$\mathcal{F}\{f_1, f_2, \dots, f_d\}$$，对任意一个函数 ****$$f \in \mathcal{F}$$ ****至少以概率 $$1 - \delta $$ ****以下不等式成立。

$$
R(f) \leq \hat{R}(f) + \varepsilon (d, N, \delta)
$$

其中 $$\varepsilon (d, N, \delta) = \sqrt{\frac{1}{2N}(\log d + \log \frac{1}{\delta})}$$ 。

