Matplotlib
作用：画图
使用 matplotlit 下的 pyplot 画
```
import matplotlib.pyplot as plt

plt.plot(x, y, color='red', linestyle='--', linewidth=5)		 	# 根据 x y 绘制二维图

plt.xlim(0,4)
plt.ylim(0,4)			# 设置初始 x y 坐标轴

plt.xlabel('herer x')
plt.ylabel('herer y')	# 设置 x 轴 y 轴 label

plt.xticks([1,3,5])
plt.yticks([1,3,9],['$normal$','$good$','$realy \ good$'])		# 自定义 x 轴 y 轴内容（某尺度对应的内容）

设置坐标轴 gca = 'get current axis'
显示 x、y 坐标轴
ax = plt.gca()
ax.spines['right'].set_color('none')
ax.spines['top'].set_color('none')
ax.xaxis.set_ticks_position('bottom')
ax.yaxis.set_ticks_position('left')
ax.spines['bottom'].set_position(('data',0))
ax.spines['left'].set_position(('data',0))


plt.show()			# 展示
```

展示的图片窗口 （名字叫 figure）
可以通过 plt.figure() 来画出多张图