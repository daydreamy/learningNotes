Numpy 学习

```py
import numpy as np
def npsum():
    a=np.array([0, 1, 2, 3])
    b=np.array([4, 5, 6, 7])
    c=a**2 + b**3
    return c
print(npsum())

data = np.array([[0, 1, 2, 3],
                [4, 5, 6, 7]])
print(data.shape)
print(data.size)
print(data.itemsize)    # 字节大小
print(np.average(data,axis=0,weights=[1,2]))  # 计算加权平均
a=np.arange(100).reshape(5, 20)

np.random的随机函数
rand(10)   [0-1]随机float
randn(10)   正态分布随机数
randint(1,10,[3,5])   [1-10]之间3行5列的随机整数
np.gradient()  # 梯度、斜率

数组计算函数
np.sqrt(arr)	# 相当于arr**0.5
np.square(arr)	# arr**2
subtract		# 减法
multiply		# 数组元素相乘

np.unique(x)		# 计算x中的唯一元素
np.tersect1d(x,y)	# 计算公共元素
```

# 一、把数组转化为矩阵
```py
array = np.array(arr)
print(array.ndim)		# 维度
print(array.shape) 	# （行，列）
print(array.size)		# 元素数量
```

# 二、创建  定义 dtype（默认64）
```py
arr = np.array([1, 2, 3], dtype = np.int)
arr = np.array([1, 2, 3], dtype = np.float32)
Zero = np.zeros((3,4))			# 参数是 （行，列）
Empty = np.empyt((3,4))		# 几乎为0的矩阵
one = np.ones((3,4))			# 全是 1 的矩阵
Range = np.arange(1,10,2)	# 类似python range
Linespace = np.linspace(1,3,3)	# 生成初始值为1，结束值为3，有三个元素的等步长 list
np.random.random((1,4))		# 生成一个 一行四列的 随机矩阵

.reshape						# 改变形状
.flatten()					# 拉开矩阵
```
# 三、运算
```py
a+b
a-b
a.dot(b)	| np.dot( a, b )	# a b 矩阵相乘
a * b						# a 每一位乘 b 每一位
a ** n					# a 的 n 次方
a.cumsum()				# 每一位累加和 并 存成一个 一维 矩阵
A.diff()					# 相邻两个数的差

```
```py
a.sum(axis = 0) | np.sum(a, axis = 0)
a.max() | np.max(a)
a.min() | np.min(a)
a.mean()						# 平均值
a.average()					# 平均值
a.median()					# 中位数
```
```py
s = np.sin(a)
c= np.cos(a)
t= np.tan(a)
```
```py
a.clip( 5, 9 ) | np.clip( a, 5, 9 )		# 矩阵 小于 5 的变成 5，大于 9 的编程 9.
print(a<25)						# 判断每一位 > < 或 == 某个值 返回一个 True False 的矩阵
```
```py
a.T | np.transpose(a)				# 转制
```

```py
a.argmin(axis) | np.argmin(a)		# 最小值的索引
a.argmax() | np.argmax(a)			# 最大值的索引
```

# 四、合并/分割
```py
np.hstack((a,b))					# 横 合并
np.vstack((a,b))					# 竖 合并
np.concatenate((a, a, b), axis=0)	# 通过数字决定是横向还是纵向合并
```
```py
np.vsplit(a,3)
np.hsplit(a,2)
np.split(a,3,axis = 0)				# 把 a 等量分割 3 分
np.array_split(a,2,axis = 0)		# 把 a 不等量分割 2 分
```