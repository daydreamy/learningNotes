css Module

CSS Modules 提供各种插件，支持不同的构建工具。 Webpack 的css-loader插件对 CSS Modules 的支持最好，而且很容易使用。
安装 npm install css-loader style-loader --save-dev

小知识
1、!：使用!作为loaders与资源之间的分隔。是“先后”的意思。
2、?：通过使用?将查询字符串附加在loader后，对其进行配置；就当做是传给他的参数来理解就好。

开始使用

1、配置全局唯一类名（哈希值）

	{
	 	test: /\.css$/,
	 	loader: "style-loader!css-loader?modules"
	}

2、如果一个类名就想叫title 不想被编成哈希值怎么办嘞
	只要加上:global即可

	.title {
 	    color: red;
	}

	:global(.title) {
	  color: green;
	}

3、订制哈希值（想自定义一个炫酷哈希值咋办嘞）

	{
      	test: /\.css$/,
      	loader: "style-loader!css-loader?modules&localIdentName=[path][name]---[local]---[hash:base64:5]&sourceMap"
 	}

其中
	[path] 是文件路径+ “-”
	[name] 是文件名字
	[local] 是被编译的类名
	[hash:base64:5] 是哈希值
为了方便调试 加入了 sourceMap，让压缩后的文件和压缩前有关联。

4、cssModule里面的样式能继承嘛
	当然可以

	.background {
	 	background-color: blue;
	}

	.title {
 		 composes: background;
		 color: red;
	}

这样title 类的背景颜色也是蓝色啦。

5、那在4的基础上能挎文件继承嘛
当然可以
文件 another.css

	.background {
		 background-color: blue;
	}

引入 anothoer.css里面的样式

	.title {
 		 composes: background from './another.css';
  		color: red;
	}

6、想在css里定义变量怎么办嘞
	CSS Modules 支持使用变量，不过需要安装 PostCSS 和 postcss-modules-values

	npm install --save postcss-loader postcss-modules-values

	{
        		test: /\.css$/,
        		loader: "style-loader!css-loader?modules!postcss-loader"
	}

接下来就可以定义变量啦
	colors.css里定义颜色
		@value blue: #0c77f8;
		@value red: #ff0000;
		@value green: #aaf200;

当前css里使用这些定义好的颜色
		@value colors: "./colors.css";
		@value blue, red, green from colors;
		.title {
  			 color: red;
			 background-color: blue;
		}