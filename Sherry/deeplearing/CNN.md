Deeplearning
# CNN
## 感知器
感知器----人工神经元；

特征：多输入（每个输入有自己的权重 ω），单一输出，通过输出与阈值比较决定真与假。

偏置 b：- 阈值。

感知器实现与非门：

![image](https://raw.githubusercontent.com/daydreamy/learningNotes/master/Sherry/static/deep01.png)

从而实现二进制：

![image](https://raw.githubusercontent.com/daydreamy/learningNotes/master/Sherry/static/deep02.png)

虽然实现二进制就可以像其他设备一样强大，但是然并卵依旧只是二进制。其实牛逼之处在于我们可以设计**学习算法**：能够自动调整人工神经元（感知器）的权重 ω和偏置 b。

## S型神经元
![image](https://raw.githubusercontent.com/daydreamy/learningNotes/master/Sherry/static/deep03.png)

出现背景：因为感知器的输出结果只有 0、1。感知器权重 ω 和偏置 b 进行小小调整时，有可能引起结果反转，引发重大连锁。不稳！希望 △ω||△b 只会影响 △output

特征：多输入（但是输入不再是 0 || 1 而是 [ 0, 1 ] ），单一输出（ 也不再是 0 || 1 而是 σ( ω*x + b)）。

这里 σ 被称为 s型函数，定义为：

![image](https://raw.githubusercontent.com/daydreamy/learningNotes/master/Sherry/static/deep04.png)

理解  σ  函数的形状很重要：

![image](https://raw.githubusercontent.com/daydreamy/learningNotes/master/Sherry/static/deep05.png)

## 神经网络结构
总体分为：输入层（左边）、输出层（右边）、隐藏层（中间）。

**主意**：由于历史的原因，尽管神经网络是由 S 型神经元构成而不是感知器，这种多层网络有时被称为多层感知器或者 MLP。

前馈神经：以上一层的输出作为下一层的输入。

## 梯度下降法
学习率 η
