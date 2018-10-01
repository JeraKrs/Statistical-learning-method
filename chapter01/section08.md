# 1.8 分类问题

分类器（classifier）：分类模型或分类决策函数。

分类（classification）：分类器对新的输入进行预测（prediction）。

类（class）：可能输出。

评价分类器性能的指标一般是分类准确率（），即对给定的测试数据集，分类器正确分类的样本数与总样本数之比。

|  | 正类预测 | 负类预测 |
| :--- | :--- | :--- |
| 正类 | TP | FN |
| 负类 | FP | TN |

* 准确率（accuracy）： $$A = \frac{TP + TN}{TP + FN + FP + TN}$$ 
* 精确率（precision）： $$P = \frac{TP}{TP + FP}$$ 
* 召回率（recall）： $$R = \frac{TP}{TP + FN}$$ 
* F1值，精确率和召回率的调和均值： $$\frac{2}{F_1} = \frac{1}{P} + \frac{1}{R} \Rightarrow F_1 = \frac{2TP}{2TP + FP + FN}$$ 



