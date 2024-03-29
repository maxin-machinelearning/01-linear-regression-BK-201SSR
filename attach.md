### 1.1线性回归

#### 1、作业内容

目的：

- 熟悉python的用法
- 熟悉 numpy

要求：

- 使用 numpy 实现线性回归模型
- 数据要求：

- - 教材数据
  - 任意数据集数据

- 代码要求，使用向量化数据实现
- 文档要求：写出推导过程**【必修】**

#### 2、推导过程

##### 1.线性回归模型

$$
给定任意样本\;X = (x_1,x_2,...,x_m)^T\;此时的线性模型为:\\
f(x)=w_1x_1+w_2x_2+...+w_mx_m\\
即为:f(X) = W^TX\\
其中\;W = (w_1,w_2,...,w_m)^T为参数(权重)向量
$$

##### 2.最小二乘估计

$$
对线性回归模型f(X)进行优化计算的目标函数定义为:  \\
J(W) = \sum_{i=1}^{n}{[(y_i-f(X_i)]^2}  \\
将上述损失函数转化为:  \\
J(W) = (y-AW)^T(y-AW)  \\
即转化为如下求解最优化问题:  \\
arg\;min_w\,J(W) = arg\;min_w\,(y-AW)^T(y-AW)  \\
令J(w)对参数向量w各分量的偏导数为0，即:  \\
\frac{\partial J}{\partial W} = A^T(y-AW) = 0\;解得:  \\
W=(A^TA)^{-1}A^Ty  \\
即为参数向量的最小二乘估计值
$$

#### 3、注意事项

1.本次作业用了两个数据集，一个来源于教材P65，一个来源于已上传的xlsx文件

#### 4、运行结果

数据一系数矩阵: [0.94618792 0.09047071] 

数据二系数矩阵: [ 0.99397832 -0.22023935] 

数据一调包系数矩阵: [0.94618792 0.        ] 

数据二调包系数矩阵: [0.99397832 0.        ]

[^数据一计算结果图]: 

![数据一计算结果图](\图片结果\数据一计算结果图.png)

[^数据二计算结果图]: 

![数据二计算结果图](\图片结果\数据二计算结果图.png)

[^数据一调包结果图]: 

![数据一调包结果图](\图片结果\数据一调包结果图.png)

[^数据二调包结果图]: 

![数据二调包结果图](\图片结果\数据二调包结果图.png)

#### 5、实验总结

##### **5.1、讲解前**

1.第一次实验走了许多弯路（大部分时间消耗在对最小二乘法原理的理解失误以及对代码的调试），最后发现代码计算预测值时错误将参数向量进行了交换，导致结果错误。

2.由上述（1）：结果误以为用最小二乘法需要迭代，进而导致研究梯度下降，结果越走越远……最后浏览教材并利用其中的数据进行第二次实验，最终发现了问题所在，同时也更深入的理解了最小二乘法的原理。

3.此次实验更深入了解到numpy对矩阵的处理，线性回归最小二乘法的原理，调包的强大以及一些细节的问题。利用python直接写出最后的推导公式所对应的相关代码，直接求出参数向量，得到答案。

4.有关封装代码的部分有些疑问，看似容易实则艰难。机器学习其修远兮，吾将推了又推……

##### 5.2、讲解后

1.求逆：np.linalg.inv 我：np.matrix().I

2.矩阵点乘:：@ 我：np.dot()

3.np.linalg.norm(x,axis=,ord=,keepdims=)用于求解范数(x：矩阵，axis：按列/按行，ord：几范数，keepdims：是否保持二位特性)
