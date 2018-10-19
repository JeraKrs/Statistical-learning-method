# 4.1 朴素贝叶斯法的学习与分类

朴素贝叶斯（naive Bayes）法是基于贝叶斯定理与特征条件独立假设的分类方法。

#### 4.1.1 基本方法

朴素贝叶斯法通过训练数据集学习联合概率分布 $$P(X, Y)$$ ，具体有：

1. 学习先验概率分布： $$P(Y = c_k)$$ 
2. 学习条件概率分布： $$P(X = x | Y = c_k) = P(X^{(1)} = x^{(1)}, \dots, X^{(n)} = x^{(n)} | Y = c_k)$$ 
3. 计算后验概率分布： $$P(Y = c_k | X = x) = \frac{P(X = x | Y = c_k)P(Y = c_k)}{\sum_k P(X = x | Y = c_k)P(Y = c_k)}$$ 
4. 获得朴素贝叶斯分类器： $$y = f(x) = arg \underset{c_k}{max} P(Y = c_k | X = x)$$ 

#### 4.1.2 后验概率最大化的含义

朴素贝叶斯法将实例分到后验概率最大的类中，即等价于期望风险最小化。

期望风险： $$R_{exp}(f) = E[ L(Y, f(x))] = E_X[\sum^K_{k=1}L(c_k, f(x))]P(c_k | X)$$ 

$$
f(x) = arg\underset{y \in Y}{min} \sum^K_{k=1} L(c_k, y)P(c_k | X = x) \\
\Rightarrow arg\underset{y \in Y}{min} \sum^K_{k=1}P(y \neq c_k | X = x) \\
\Rightarrow arg\underset{y \in Y}{min}(1 - P(y \in c_k | X = x) \\
\Rightarrow arg\underset{y \in Y}{max} P(y = c_k | X = x)
$$



