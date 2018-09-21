# 2.4 习题

#### 2.4.1

异或不具有线性可分性，所以感知机不能表示异或。

#### 2.4.2

```text
# coding: utf-8
import numpy as np

class Perceptron:
    def __init__(self, X, Y, eta=1):
        self.X = X
        self.Y = Y
        self.W = np.zeros([X.shape[1], 1])
        self.B = np.zeros([1, 1])
        self.eta = 1
    
    def negative(self, ):
        for i in range(self.X.shape[0]):
            if self.Y[i] * (np.dot(self.X[i], self.W) + self.B) <= 0:
                return True, i
        return False, 0
    
    def train(self,):
        i = 0
        while i < 100:
            flag, k = self.negative()
            if flag == False:
                break
            i = i + 1
            
            self.W = self.W + (self.eta * self.Y[k] * self.X[k]).reshape(p.W.shape)
            self.B = self.B + (self.eta * self.Y[k]).reshape(p.B.shape)
    
    def output(self, ):
        print("W=\n{}\n".format(self.W), "B=\n{}\n".format(self.B))

X = np.array([(3, 3), (4, 3), (1, 1)])
Y = np.array([1, 1, -1])

p = Perceptron(X, Y)
p.train()
p.output()
```

#### 2.4.3

点集 $$X = \{x_1, \dots, x_n\}$$ 有凸包 $$conv( X) = \{x = \sum_{i=1}^{k} \lambda_i x_i | \sum_{i=1}^k\lambda_i = 1, \lambda_i \geq 0\}$$ 

若训练数据 $$T$$ 线性可分，则有超平面 $$S = \{x | w \cdot x + b = 0\}$$ 满足

$$
\left\{\begin{matrix}
w \cdot x_i + b \geq \varepsilon  & \forall x_i \in \{x_i | y_i = 1\} \\
w \cdot x_i + b \leq \varepsilon  & \forall x_i \in \{x_i | y_i = -1\}
\end{matrix}\right.
$$

对于正实例的点组成的凸包可表示为 $$conv(X^+) = \{x = \sum^k_{i=1}\lambda_ix_i | \sum_{i=1}^k\lambda_i = 1, \lambda_i \geq 0, y_i = 1\}$$ ，且对凸包内的点有 $$w \cdot x + b =\sum^k_{j=1} \lambda_j w \cdot x_j + b \geq \sum^k_{j=1}\lambda_j \varepsilon \geq 0$$ ；对负实例有 $$w \cdot x + b \leq 0$$ 。

