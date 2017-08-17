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
### list
list = [1, 2, 3]
len ( list )    				对应js array.lengh  获得list（数组）长度。
list[-1]				获得 list 最后一个元素。
list.insert(1, 'Jack’)		在第一位 插入 jack，之前的第一位变成第二位。
list.pop()				推出最后一位。
list.pop( i )				推出第 i 位。

### tuple
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
for i in list：其中 i 是 list 的各项，不是index。
while True/False : 如果为 True 就继续做。False就跳出循环；同样有 break 和 continue。
range(101)：生成 0-100 整数序列。

## dict（字典 json）和 set（）
### dict 和 json 的区别:
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

