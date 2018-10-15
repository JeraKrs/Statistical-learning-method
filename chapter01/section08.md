# 1.8 分类问题

在监督学习中，当输出变量 $$Y$$ 取有限个离散值时，预测问题便成为分类问题。监督学习从数据中学习一个分类模型或分类函数，成为**分类器（classifier）**；分类器对新的输入进行输出的预测（prediction），称为**分类（classification）**；可能输出的称为**类（class）**。

评价分类器性能的指标一般是分类**准确率（accuracy）**，即对给定的测试数据集，分类器正确分类的样本数与总样本数之比。

|  | 正类预测 | 负类预测 |
| :--- | :--- | :--- |
| 正类 | TP | FN |
| 负类 | FP | TN |

* 准确率（accuracy）： $$A = \frac{TP + TN}{TP + FN + FP + TN}$$ 
* 精确率（precision）： $$P = \frac{TP}{TP + FP}$$ 
* 召回率（recall）： $$R = \frac{TP}{TP + FN}$$ 
* F1值，精确率和召回率的调和均值： $$\frac{2}{F_1} = \frac{1}{P} + \frac{1}{R} \Rightarrow F_1 = \frac{2TP}{2TP + FP + FN}$$ 



