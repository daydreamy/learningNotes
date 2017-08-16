一点点
# 出发
## print()
输出，可以写表达式，类似console.log。
## input()
输入，比如 name = input(“print your name:”)。 其中参数为提示内容，输入内容后点回车会把值传给name。
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

list 和 tuple