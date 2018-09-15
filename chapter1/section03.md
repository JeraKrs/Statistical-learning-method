# 1.3 统计学习三要素

方法=模型+策略+算法

#### 1.3.1 模型

模型是所要学习的条件概率分布或决策函数。

模型的假设空间（hypothesis space）包含所有可能的条件概率分布或决策函数。

$$
\mathcal{F} = \{ f | Y = f(X)\}
$$

其中 $$X, Y$$ 分别为输入和输出空间上的变量， $$\mathcal{F}$$ 通常是由一个参数向量决定的函数族，可表示为：

$$
\mathcal{F} = \{ f | Y = f_{\theta}(X), \theta \in R^n\}
$$

参数向量 $$\theta$$ 取值于 $$n$$ 维欧氏空间 $$R^n$$ ，称为参数空间（parameter space）。

#### 1.3.2 策略

**损失函数和风险函数**

对于给定的输入 $$x$$ ，由 $$f(x)$$ 给出相应的 $$y$$ ，这个输出的预测值 $$f(x)$$ 与真实值 $$y$$ 可能不一致。

损失函数（loss function）或代价函数（cost function）来度量预测错误的程度，它是 $$f(X)$$ 和 $$Y$$ 的非负实值函数 $$L(Y, f(X))$$ 。

* 0-1损失函数（0-1 loss function）：

$$
L(Y, f(X)) = \left\{\begin{matrix} 1 & f(x) \neq y \\  0 & f(x) = y \end{matrix}\right.
$$

* 平方损失函数（quadratic loss function）：

$$
L(Y, f(X)) = (y - f(x))^2
$$

* 绝对损失函数（absolute loss function）：

$$
L(Y | f(X)) = | y - f(x)|
$$

* 对数损失函数（logarithmic loss function）或对数似然损失函数（loglikelihood loss function）：

$$
L(Y, P(Y|X)) = -\log P(y|x)
$$

损失函数值越小，模型越好。因为假定 $$X, Y$$ 服从联合概率分布 $$P(X, Y)$$，损失函数的期望为

$$
R_{exp}(f) = E_{P}[ L(Y, f(X)] = \int_{\mathcal{X} \times \mathcal{Y}} L(y, f(x))P(x, y)dxdy
$$

这是理论上模型 $$f(x)$$ 关于联合分布 $$P(X, Y)$$ 的平均意义下的损失，称为风险函数（risk function）或期望损失（expected loss）。统计学习方法的目标就是选择期望风险最小的模型。

由于 $$P(Y|X)$$ 未知（如果已知联合概率分布的话，就无需学习），所以需要通过经验风险（empirical risk）或经验损失（empirical loss）来评估模型：

$$
R_{emp}(f) = \frac{1}{N} \sum^N_{i=1} L(y_i, f(x_i))
$$

经验风险或经验损失是模型训练样本集的平均损失，根据大数定律，当 $$N \rightarrow \infty$$ ， $$R_{emp}(f) \rightarrow R_{exp}(f)$$ 。

**经验风险最小化与结构风险最小化**

经验风险最小化（empirical risk minimization，ERM）：经验风险最小的模型为最优的模型

$$
\underset{f \in \mathcal{F}}{min} \frac{1}{N}\sum^{\infty}_{i=1}L(y_i, f(x_i))
$$

例如极大似然估计（maximum likelihood estimation）。但这种策略在样本容量很小时，往往会出现过拟合（over-fitting）的现象。

结构化最小化（structural risk minimization，SRM）：为了防止过拟合的策略，它等价于正则化（regularization），在

