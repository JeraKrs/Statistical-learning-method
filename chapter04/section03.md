# 4.3 习题

#### 4.3.1

证明 $$P(Y = c_k) = \frac{\sum^N_{i=1}I(y_i = c_k)}{N}$$ 

设分类属于 $$c_k$$ 的概率为 $$\theta_k$$ ，则对于训练数据集有 $$P = \theta^M_k(1-\theta_k)^{N-M}$$ ，其中 $$M = \sum^N_{i=1}I(y_i = c_k)$$ 。

$$
arg\underset{\theta_k}{max} P = arg\underset{\theta_k}{max} (\theta^M_k(1-\theta_k)^{N-M}) \\ 
\Rightarrow \theta_k = \frac{M}{N} =  \frac{\sum^N_{i=1}I(y_i = c_k)}{N}
$$

同理可得 $$P(X^{(j)} = a_{jl}|Y = c_k) = \frac{\sum^N_{i=1}I(x_i^{(j)} = a_{jl}, y_i = c_k)}{\sum^N_{i=1}I(y_i = c_k)}$$ 。

#### 4.3.2

证明 $$P_{\lambda}(Y = c_k) = \frac{\sum^N_{i=1}I(y_i = c_k) + \lambda}{N + K\lambda}$$ 

首先，加入先验概率，在没有任何信息的情况下假设先验概率为均匀分布： $$P(Y = c_k) = \frac{1}{K}$$ ，则有 $$K P(Y = c_k) = 1$$ 。

考虑极大似然估计的条件约束 $$P(Y=c_k) = \frac{\sum^N_{i=1}I(y_i = c_k)}{N} = N P(Y = c_k) \sum^N_{i=1}I(y_i = c_k)$$ 。

结合两个约束条件有 

$$
\lambda(K P(Y = c_k) - 1) + N P(Y = c_k) - \sum^N_{i=1}I(y_i = c_k) = 0 \\
\Rightarrow P_{\lambda}(Y = c_k) = \frac{\sum^N_{i=1}I(y_i = c_k) + \lambda}{N + K\lambda}
$$

同理可证 $$P_{\lambda}(X^{(j)} = a_{jl} | Y = c_k) = \frac{\sum^N_{i=1} I(x_i^{(j)} = a_{jl}, y_i = c_k) + \lambda}{\sum^N_{i=1}I(y_i = c_k) + S_j\lambda}$$ 。

