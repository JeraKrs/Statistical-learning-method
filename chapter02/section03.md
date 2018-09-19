# 2.3 感知机学习的算法

#### 2.3.1 感知机学习算法的原始形式

感知机学习算法是误分类驱动的，具体采用梯度下降法（stochastic gradient descent）：

* 任取超平面 $$w_0, b_0$$ 
* 用梯度下降法不断地极小化目的函数

注：不是一次使用 $$M$$ 中所有的误分类点，而是一次随机选取一个误分类点。

假设五分类点集固定，那么损失函数 $$L(w, b)$$的梯度有 $$\bigtriangledown_{w} L(w, b) = - \sum_{x_0 \in M} y_ix_i, \bigtriangledown_{b} = -\sum_{x_i \in M}y_i$$，每次随机选取一个误分类点 $$(x_i, y_i)$$对 $$w, b$$进行更新 $$w \leftarrow w + \eta y_i x_i, b \leftarrow b + \eta y_i$$,其中 $$\eta$$ 为步长（$$0 < \eta \leq 1$$），也称学习率（learning rate）。

**算法-2.1 （感知机学习算法的原始形式）**

输入：训练数据集 $$T = \{ (x_1, y_1), (x_2, y_2), \dots, (x_n, y_n)\}$$，其中 $$x_i \in \mathcal{X} = R^n, y_i \in \mathcal{Y} = \{+1, -1\}$$ ；学习率 $$\eta$$ ，其中 $$0 < \eta \leq 1$$ 。

输出： $$w, b$$ ；感知机模型 $$f(x) = sign(w \cdot x + b)$$ 。

1. 选取初值 $$w_0, b_0$$ 
2. 在训练集中选取数据 $$(x_i, y_i)$$ 
3. 如果 $$y_i(w\cdot x_i + b) \leq 0$$ ，则 $$w \leftarrow w + \eta y_i x_i, b \leftarrow b + \eta y_i$$ 
4. 转至第2步，直到训练集中没有误分类点

#### 2.3.2 算法的收敛性

令 $$\hat{w} = (w^T, b)^T, \hat{x} = (x^T, 1)^T$$ 

**定理-2.1（Novikoff）**

\(1\) 存在满足条件 $$||\hat{w}_{opt}|| = 1$$ 的超平面 $$S_{opt}$$ 将训练数据完全正确的分开；且存在 $$\gamma > 0$$ 对所有训练数据满足：

$$
y_i (\hat{w}_{opt} \cdot \hat{x}_i) \geq \gamma
$$

证明（1）：因为训练数据集线性可分，按照定义-2.2，存在平面可以将训练数据完全分开，取超平面 $$\hat{w}_{opt} \cdot \hat{x} = 0$$ ，使 $$||\hat{w}_{opt}|| = 1$$ ；由于对有限的训练数据集有 $$y_i(\hat{w}_{opt} \cdot \hat{x}_i) > 0$$，所以存在

$$
\gamma = \underset{i}{min}\{y_i(w_{opt}\cdot x_i + b_{opt})\}
$$

\(2\) 令 $$R = \underset{1 \leq i \leq n}{max}||\hat{x}_i||$$ ，则感知机算法2.1在训练数据集上的误分类次数 $$k$$ 满足不等式

$$
k \leq (\frac{R}{\gamma})^2
$$

证明（2）：首先有推导两个不等式

$$
A: \hat{w}_k \geq k\eta\gamma \\
\hat{w}_{k} = \hat{w}_{k-1} + \eta y_i \hat{x}_i \\
\Rightarrow \hat{w}_k\hat{w}_{opt} = \hat{w}_{k-1}\hat{w}_{opt} + \eta y_i \hat{w}_{opt} \hat{x}_i \\
\Rightarrow \hat{w}_k\hat{w}_{opt} \geq \hat{w}_{k-1}\hat{w}_{opt} + \eta \gamma \\
\Rightarrow \hat{w}_k\hat{w}_{opt} \geq k\eta\gamma
$$

$$
B: ||\hat{w}_k||^2 \leq k\eta^2R^2 \\
||\hat{w}_k||^2 = ||\hat{w}_{k-1}||^2 + 2\eta y_i \hat{w}_{k-1}\hat{x}_i + \eta^2||\hat{x}_i||^2 \\
\Rightarrow ||\hat{w}_k||^2 \geq ||\hat{w}_{k-1}||^2 + \eta^2||\hat{x}_i||^2\ \ \because (x_i, y_i) \in M, y_i\hat{w}_{k-1}\hat{x}_i \geq 0 \\
\Rightarrow ||\hat{w}_k||^2 \geq ||\hat{w}_{k-1}||^2 + \eta^2R^2 \\
\Rightarrow ||\hat{w}_{k}||^2 \geq k\eta^2R^2
$$

证明（Novikoff**）：**

$$
\sqrt{k}\eta R \geq ||\hat{w}_k|| \geq k \eta \gamma \\
\Rightarrow k\eta^2R^2 \geq k^2\eta^2\gamma^2 \\
\Rightarrow k \leq (\frac{R}{\gamma})^2
$$

#### 2.3.3 感知机学习算法对偶形式

**算法-2.2（感知机学习算法对偶形式）**

输入：数据集 $$T = \{(x_1, y_1), (x_2, y_2), \dots, (x_n, y_n)\}$$ ，其中 $$x_i \in R^n, y_i \in \{+1, -1\}$$ ；学习率 $$\eta$$ ，其中 $$0 < \eta \leq 1$$ 。

输出： $$\alpha, b$$ ；感知机模型 $$f(x) = sign(\sum^n_{i=1}\alpha_i y_i x_i \cdot x + b)$$ 。

1. 选取初值 $$\alpha \leftarrow 0, b \leftarrow 0$$ 
2. 在训练集中选取数据 $$(x_i, y_i)$$ 
3. 如果 $$y_i (\sum^n_{j=1} \alpha_j y_j x_j \cdot x_i + b) \leq 0$$ ，则 $$\alpha_i = \alpha_i + \eta, b = b + \eta y_i$$ 
4. 转至第2步，直到训练集中没有误分类点



