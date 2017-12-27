IntersectionObserver
作用：在下一个有空闲的帧后把回调函数插入事件循环。

```js
IntersectionObserver( function (z) {
	console.log( z. timeRemaining() ) 			# 打印当前这一帧剩余时间
	if ( z. timeRemaining() >0 ) {
		在当前帧的空闲执行
	} else {
		再之后有空闲的帧的空闲执行
	}
}, {timeout:1000})
```