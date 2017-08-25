# requestAnimationFrame 和 tween
## 序言 requestAnimationFrame 厉害的地方
HTML5标准规定了setTimeout()的第二个参数的最小值（最短间隔），不得低于4毫秒，如果低于这个值，就会自动增加。在此之前，老版本的浏览器都将最短间隔设为10毫秒。另外，对于那些DOM的变动（尤其是涉及页面重新渲染的部分），通常不会立即执行，而是每16毫秒执行一次。这时使用requestAnimationFrame()的效果要好于setTimeout()。

## 兼容
```js
window.requestAnimationFrame = window.requestAnimationFrame || window.mozRequestAnimationFrame || window.webkitRequestAnimationFrame || window.msRequestAnimationFrame;
```
## 心得
requeseAnimationFrame(go) 方法会在运行后会向浏览器请求下一帧运行 go 方法，并传入一个参数 time。time = 运行 go 的时间 -- 运行 requeseAnimationFrame(go) 的时间。

```js
var i = 0
function go(time){
     console.log(i)
      i++
      console.log(time)
      if(time<2000){
          requestAnimationFrame(go)
      }
}
requestAnimationFrame(go)
```

通过例子可得：请求每一帧的间隔时间并不是固定的，并且也不是整数，所以不便于拿他做为运动的自变量。

*透过现象看本质*

变速运动运动实际上就是速度随时间变化的函数 vt = f(t)；路程 s = ∫f(t)

那么通过 requeseAnimationFrame 实现运动的方法就变成了

```js
var current = 0,during = 10,s;
function go(){
    s = f(current);
    ...
    current++;
    if(current<=during){
        requestAnimationFrame(go)
   }
}
requestAnimationFrame(go)
```

*是不是已经心潮澎湃了，只要有 f(x) 的算法我们就可以做各种运动了，不要慌，造轮子的事情是一定早就有人做过的，请继续往下看*

* * *

# tween
网上的tween、tweenLite 实在种类繁杂。但是大同小异，都是一个饱含各种通过时间 t 得到当前位置 s 的函数的库。

## 栗子：

```js
t: current			//(初试时间)
b: beginning value	//(初始值)
c: change value		//(变化量)
d: duration			//(持续时间)

function easeOut (t, b, c, d) {
                    return -c * ((t = t/d - 1) * t * t*t - 1) + b
}
```
首先明确这是一个算出 路程 s 与时间 t 关系的函数 s = f(t)；可以对应 s = 1/2 gt^2。

简化公式可得
```
s = c * [1 - (1-t/d)^4] + b

```

上面函数本质为
```
s = c*f(t) + b
```
f(t) 为  [1 - (1-t/d)^4] ，可分解为 (1-t/d)^4 和 1-t/d，对应下图。

![image](https://raw.githubusercontent.com/daydreamy/learningNotes/master/Sherry/static/fx.png)

*可得*：
```
f(t) 的结果／ f(t) 的最大值（1）= 当前应该变化到的量 ／需要变化的总量 （c）。
当前量（s） = 当前应该变化到的量 + 初始值（b）
```

## 总结
Tween 里的每一个函数都是一个可以对应成图像的数学公式，描述的都是路程随时间变化的变化。