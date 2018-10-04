# 4.1 朴素贝叶斯法的学习与分类

朴素贝叶斯（naive Bayes）法是基于贝叶斯定理与特征条件独立假设的分类方法。

#### 4.1.1 基本方法

通过训练数据集学习联合概率分布 $$P(X, Y)$$ ：

* 先验概率分布： $$P(Y = c_k)$$ 
* 条件概率分布： $$P(X = x | Y = c_k)$$ 
* 后验概率分布： $$P(Y = c_k | X = x) = \frac{P(X = x | Y = c_k)P(Y = c_k)}{\sum_k P(X = x | Y = c_k)P(Y = c_k)}$$ 
* 朴素贝叶斯分类器： $$y = f(x) = arg \underset{c_k}{max} P(Y = c_k | X = x)$$ 

#### 4.1.2 后验概率最大化的含义

朴素贝叶斯法将实例分到后验概率最大的类中，即等价于期望风险最小化。

期望风险： $$R_{exp}(f) = E[ L(Y, f(x))] = \sum^K_{k=1}L(c_k, f(x))P(c_k | X)$$ 

$$
f(x) = arg\underset{y \in Y}{min} \sum^K_{k=1} L(c_k, y)P(c_k | X = x) \\
\Rightarrow arg\underset{y \in Y}{min} \sum^K_{k=1}P(y \neq c_k | X = x) \\
\Rightarrow arg\underset{y \in Y}{min}(1 - P(y \in c_k | X = x) \\
\Rightarrow arg\underset{y \in Y}{max} P(y = c_k | X = x)
$$



