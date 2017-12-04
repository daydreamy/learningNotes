一点点
# 出发
## print()

输出，可以写表达式，类似console.log。

## input()

输入，比如 name = input(“print your name:”)。 其中参数为提示内容，输入内容后点回车会把值传给name。（此时 name 的数据类型为字符串）

# 基础
## 数据类型
### 布尔值
True & False

tips:

	>>> int('123')
	123
	>>> int(12.34)
	12
	>>> float('12.34')
	12.34
	>>> str(1.23)
	'1.23'
	>>> str(100)
	'100'
	>>> bool(1)
	True
	>>> bool('')
	False

## 字符串和编码
### 编码

	\#!/usr/bin/env python3
	\# -\*- coding: utf-8 -\*-

第一行注释是为了告诉Linux/OS X系统，这是一个Python可执行程序，Windows系统会忽略这个注释；

第二行注释是为了告诉Python解释器，按照UTF-8编码读取源代码，否则，你在源代码中写的中文输出可能会有乱码

### 字符串中的占位符
例：

	>>> 'Hello, %s' % 'world'
	'Hello, world'
	>>> 'Hi, %s, you have $%d.' % ('Michael', 1000000)
	'Hi, Michael, you have $1000000.'

用法：前面用占位符占位，后面使用%()传入想写的数据。

占位符规则：

	%d	整数
	%f	浮点数
	%s	字符串
	%x	十六进制整数

tips：

如果你不太确定应该用什么，%s永远起作用，它会把任何数据类型转换为字符串。

有些时候，字符串里面的%是一个普通字符怎么办？这个时候就需要转义，用%%来表示一个%。

	>>> 'growth rate: %d %%' % 7
	'growth rate: 7 %'

## list（数组） 和 tuple（内容不能改）
### list []

list = [1, 2, 3]

len ( list )    				对应js array.lengh  获得list（数组）长度。

list[-1]					获得 list 最后一个元素。

list.insert(1, 'Jack’)		在第一位 插入 jack，之前的第一位变成第二位。

list.append(5)			类似 js push(5)

list.pop()				推出最后一位。

list.pop( i )				推出第 i 位。

list.index(“a”)			返回 “a” 在 list 中的位置

#### tips
```
解构赋值 a, b, c = [1, 2, 3] 对应 js var [a, b, c] = [1, 2, 3]
```

### tuple ()
tuple和list非常类似，但是tuple一旦初始化就不能修改。

tips：

如果要定义一个空的tuple，可以写成()：

	>>> t = ()
	>>> t
	()

要定义一个只有1个元素的tuple 要写成 (1, )，不然会被理解成 赋值。

	>>> t = (1,)
	>>> t
	(1,)

注意 tuple 里面可以存 list ，而这个 list 里的值可以修改。是因为，无论如何修改，list 的地址不会变。

## 条件语句
注意：

没有大括号 { } 都是冒号 :

最好别写小括号。

elif 对应js 中 else if

	a = 10
	if a > 5:
	    print ("a>5")
	else:
	    print ("a<5")

## 循环
在 py 中没有和 js 一样的 for (var I=0, I<10; I++){} 这种循环。只有两种：for in 和 while

for i in list：其中 i 是 list 的各项，不是index。

while a>0 : 条件为 True 就继续做，False就跳出循环；同样有 break 和 continue。

## dict（字典 json）和 set（无序和无重复元素的集合）
### dict 和 json 的区别:
	dic = { a:1, b:2 ,c:3}
	dic.values				# [‘a’, ‘b’, ‘c’]
	dic.values				# [1, 2, 3]
	dic.items()				# [(‘a’, 1), (‘b’, 2), (‘c’, 3)]
	dict[‘a‘] 如果不存在会报错，而不是 undefined。



两种办法判断是否存在：

	>>> ‘a’ in dict
	False

或者

	>>> dict.get(”a“, ”不存在喔”)
	>>>  不存在喔      	  # 如果不存在，返回第二个参数 如果不写第二个参数，返回空

	>>> dict.get(‘a’)
	>>>          		# 如果不存在，返回空

### set 无序和无重复元素的集合

在 python2.7 中

	>>> s = set([1,2,3])
	>>> s
	set([1, 2, 3])

在 python3 中

	>>> s = set([1,2,3])
	>>> s
	{1, 2, 3}

Tips:
set 没有 index。所以 s[0] 会报错。（TypeError: 'set' object does not support indexing
）

通过 add(value) 添加元素。

通过 remove(value) 删除元素。

set 会自动合并相同元素。所以可以做交集、并集。

	>>> s1 = set([1, 2, 3])
	>>> s2 = set([2, 3, 4])
	>>> s1 & s2
	{2, 3}
	>>> s1 | s2
	{1, 2, 3, 4}

# 函数
## 使用 def 定义函数。
## 函数的参数
### 定义的函数的参数 都是用解构赋值给与 *初值* ，不然 使用函数时候如果传入参数不全会报错

	def a (x, y):
	    print (x)
 	   return
	a(1)			# a() takes exactly 2 arguments (1 given)

	def a (x, y = 0):
	    print (x)
 	   return
	a(1)	     		# 1

	def a (x, y = 0, z = 0):
	    print (x, z)
 	   return
	a(1, z = 3 )	     		# 1, 3        但是这种操作需要知道形参的名字

*初值* 如果是对象必须指向 **不变对象** 常用 none。通过下面例子可以看出，解构的对象并不是每次重新创建的，而是懒惰的。

反例：

	def add_end(L=[]):
    		L.append('END')
    		return L

虽然

	>>> add_end([1, 2, 3])
	[1, 2, 3, 'END']
	>>> add_end(['x', 'y', 'z'])
	['x', 'y', 'z', 'END']

但是

	>>> add_end()
	['END']
	>>> add_end()
	['END', 'END']
	>>> add_end()
	['END', 'END', 'END']

正确做法：

	def add_end(L=None):
	    if L is None:
	        L = []
	    L.append('END')
	    return L

### 可变参数
可以通过给参数 加上 * 是参数变成数量可变的参数，但是如果参数本身是一个可变参数（list／tuple） 在传入的时候加上 *就可以转化啦。

	def calc(*numbers):
	    sum = 0
	    for n in numbers:
	        sum = sum + n
	    return sum

	calc(1,2,3)			# 6
	calc([1,2,3])			# TypeError: unsupported operand type(s) for +: 'int' and 'list'
	calc(*[1,2,3])			# 6

### 关键字参数  **（可传属性值对的参数）
用于收集不限个数的属性值对，在参数前面加上双星 **

	def person(name, age, **kw):
   		print('name:', name, 'age:', age, 'other:', kw)

	>>> person('Bob', 35, city='Beijing')
	name: Bob age: 35 other: {'city': 'Beijing'}

	>>> person('Adam', 45, gender='M', job='Engineer')
	name: Adam age: 45 other: {'gender': 'M', 'job': 'Engineer'}

	>>> extra = {'city': 'Beijing', 'job': 'Engineer'}
	>>> person('Jack', 24, city=extra['city'], job=extra['job'])
	name: Jack age: 24 other: {'city': 'Beijing', 'job': 'Engineer'}


### 命名关键字参数 *，obj，...
用于限制关键字参数的名字。

*我没实验成功，这个例子报错了：*

	def person(name, age, *, city='Beijing', job):
	    print(name, age, city, job)

	person('Jack', 24, job='Engineer')


# 高级特性
## 切片[:] ( 类似 js 里 slice ，但是要厉害多了)
	arr = [0, 1, 2, 3, 4, 5, 6, 7, 8];
	arr[:3]      	#  [0, 1, 2,]  			 取前三个。
	arr[-3:] 	 	#  [7, 8, 9]			 取后三个
	arr[1:]	 		#  [3, 4, 5, 6, 7, 8] 	 	从第一取到最后。
	arr[-3:-2]		#  [7]				取倒数第三个到倒数第二个（不包含倒数第二个）
 	arr[1:3]  	 	#  [1, 2]				 取第一 到第三个（不包含第三个）。
	arr[:6:2]		#  [0, 2, 4]			前 6 位，每隔 2 位取一位

## 遍历
获取数组中一个元素 （value） 的位置：

	arr.index(value)

Py中遍历只有唯一方法 for in，和js不同：

Js中
for i in 对象 i 为对象的每一位 key 值
for i of 对象 i 为对象的每一位 value 值。

回到 py
如果在遍历一个对象 { } ，可以写成

	obj = {'a': 11, 'b': 22, 'c': 33}

	for i in obj:
   		 print (i)
	# 输出 a,  c, b

	for i in obj.values():
    		print (i)
	# 输出 11, 33, 22

	for i,j in obj.items():
    		print (i,j)
	# 输出  'a', 11, 'c', 33, ‘b’, 22

因为dict的存储不是按照list的方式顺序排列，所以，迭代出的结果顺序很可能不一样。堆内存的存储空间不一定是连续的。

问题来了：

一、如何便利一个数组 arr 还想得到每一位的 key ，还不想用 arr.index(key) 方法呢？答：使用 enumerate 方法可以转化成 *索引-元素对* 如果脱离 for in 单独用，没法返回转换后的东西。

	>>> for i, value in enumerate(['A', 'B', 'C']):
		...     print(i, value)
		...
		0 A
		1 B
		2 C

判断一个对象是否能被遍历（迭代），通过collections 里的 Iterable 模块来判断。isinstance 是用来判断类型的，isinstance(A, B) 对应 js 里 A instanceof B。

	>>> from collections import Iterable
	>>> isinstance('abc', Iterable) # str是否可迭代
	True
	>>> isinstance([1,2,3], Iterable) # list是否可迭代
	True
	>>> isinstance(123, Iterable) # 整数是否可迭代
	False

## 生成列表（数组）range 的各种用法

正常：

	range(3)
	# [0, 1, 2]

选择初始值：

	range(1,3)
	# [1, 2]

使用列表表达式，设置返回数字的算法，下例中 x+x 就是为返回值设定的算法：

	[x+x for x in range(3)]
	# [0, 2, 4]


	# 当然也可以穿入函数

	def demo(z):
   		 print z
	[demo(x) for x in range(3)]
	# [1, 2, 3]

设置条件，虽然复杂条件可以写到函数里，但是简单的条件可就不用这么麻烦喽：

	[x+x for x in range(3) if x%2 == 0]
	# [0, 4]

还可以更复杂，更复杂，但是不想知道了，无论多么复杂我在外面写个函数肯定都能解决。

## 生成器 generator
背景：通过列表生成式（range），可以一下生成很长的列表，但是不一定这么长都能用得到啊，能不能用多少，算出来多少呢？于是就有了gnenrator。

生成 generator 的两种方法：

	g = (x+x for x in range(10))
	# g 就是一个generator了。

	def demo():
    		i = 0
    		while i<10:
        			yield i
       			i = i+1
	g = demo()
	# g 就是一个 generator 了。

想获得这个 generator 的下一个值，使用可以使用 next(g) 来得到，但是到最后一位以后继续调用会报错。所以只使用 for in 来得到他的所有值。( 在js中 使用 for of 来遍历generator、Set 的值们 )

## 迭代器
可以从 collection 中 import 出两个对象，分别是 Iterable 和 Iterator，可以通过 isinstance(a,b) 来看 a 是否是 b 的实例。

Iterable 是一个有限长度的。I

凡是可作用于for循环的对象都是 Iterable 类型；

凡是可作用于next()函数的对象都是 Iterator 类型，它们表示一个惰性计算的序列，他的每一个下一步的结果都是当下计算的；

# 函数式编程
## 高阶函数


### reduce
f 接受两个参数。

	reduce(f, [x1, x2, x3, x4]) = f(f(f(x1, x2), x3), x4)

### map
f 接受一个参数

	map(f, [x1, x2, x3, x4]) = [f(x1), f(x2),f(x3) ,f(x4) ]

### filter
f 接受一个参数，根据参数进行判断，返回真就留下。

	filter(f, [x1, x2, x3, x4])

### sorted
三个参数 数组、reverse（反序）、key。key传入一个f，f会依次执行数组中每一位，并根据结果进行排序。

	z = sorted([1,3,2,11,6], reverse =True, key = f )

## 匿名函数 lambda（λ）读作 [ˈlæmdə]
写法：lambda 参数 ：返回值

	lambda x: x * x

## 装饰器 decorator
在 python 中的装饰器只有类似 js 中对class的装饰器，没有类似对 class里一个方法的装饰器；但是在 python 中由于很多方法的判断逻辑依赖方法名 __ name__，所以在使用装饰漆时候要重写方法名。

	import functools

	def log(func):
	    @ functools.wraps(func)
 	   def demo(*args, **kw):
 	       print('call %s():' % func.__name__)
 	       return func(*args, **kw)
	    return demo

使用 import functools 里的 @ functools.wraps(func) 来重写方法名。

## 偏函数
当函数的参数个数太多，需要简化时，使用functools.partial可以创建一个新的函数（偏函数），这个新函数可以固定住原函数的部分参数，从而在调用时更简单。

	>>> import functools
	>>> int2 = functools.partial(int, base=2)
	>>> int2('1000000')

# 模块
## 使用模块
### 模块的书写规范
from 模块 import 方法

### 安装第三方模块
```
npm install
npm list			# 查看有哪些模块
npm freeze		# 查看有哪些安装的模块
```

# 面向对象编程
## 类和实例
类：

Class 类名 （ 从哪继承来的，一般是 object ）

	__init__ 方法 类似 constructor( self 对应this , arg ... )

	其他方法。。。

```
class Student(object):

    def __init__(self, name, score):
        self.name = name
        self.score = score
        self.__preName = name			# 私有变量

    def print_score(self):
        print('%s: %s' % (self.name, self.score))
```

实例：
student1 = Student( “name”, “80”)

## 私有变量
上一个例子中 __preName 就是一个私有变量，无法通过  student1. __preName 访问到。若想访问：
```
student1._Student__preName
```
*并没有真正的访问不到、无法修改的私有变量*，一切靠自觉。

## 继承和多态
### 继承
```
class Animail(object):
	def run():
		print("haha")

class dog(Animail):
	pass

dog.run()
```

# 高级面向对象编程
## __slots__ 插槽
作用：给 一个class 规定他的实例只允许有哪些属性和方法，不许再添加新的方法（对其子类不生效）

```
class Student(Object):
	__slots__ = (‘name’)

s = Student()
s.age = 1		# AttributeError: 'Student' object has no attribute 'age'
```

## grtter @ propoty
Py 中实现 getter 和 setter 方法为，给一个 方法 名字上 加上装饰器 @ propoty 。
```
class Student(object):

    @ property
    def birth(self):				# 把 birth 方法变为属性。birth ，对应方法为 getter
        return self._birth

    @ birth.setter				# 设置 birth 的 setter
    def birth(self, value):
        self._birth = value
```

## 多重继承
新类可以继承多个类
```
class Bird(object):
    def fly(self):
        print('i can fly')

class Dog(object):
    def run(self):
        print('i can run')

class BirdDog(Bird, Dog):
    def speak(self):
        print('i can speak')

monster = BirdDog()
monster.fly()
monster.run()
```

[还有一些高级用法略](https://www.liaoxuefeng.com/wiki/0014316089557264a6b348958f449949df42a6d3a2e542c000/00143186738532805c392f2cc09446caf3236c34e3f980f000)

# 调试
```
if __name__ == '__main__':
	print(1)    # 就可以调用各种方法了
```