Babel
Babel的包构成
### 核心包
babel-core：babel转译器本身，提供了babel的转译API，如babel.transform等，用于对代码进行转译。像webpack的babel-loader就是调用这些API来完成转译过程的。
babylon：js的词法解析器
babel-traverse：用于对AST（抽象语法树，想了解的请自行查询编译原理）的遍历，主要给plugin用
babel-generator：根据AST生成代码

### 功能包
babel-types：用于检验、构建和改变AST树的节点
babel-template：辅助函数，用于从字符串形式的代码来构建AST树节点
babel-helpers：一系列预制的babel-template函数，用于提供给一些plugins使用
babel-code-frames：用于生成错误信息，打印出错误点源代码帧以及指出出错位置
babel-plugin-xxx：babel转译过程中使用到的插件，其中babel-plugin-transform-xxx是transform步骤使用的
babel-preset-xxx：transform阶段使用到的一系列的plugin
babel-polyfill：JS标准新增的原生对象和API的shim，实现上仅仅是core-js和regenerator-runtime两个包的封装
babel-runtime：功能类似babel-polyfill，一般用于library或plugin中，因为它不会污染全局作用域

### 工具包
babel-cli：babel的命令行工具，通过命令行对js代码进行转译
babel-register：通过绑定node.js的require来自动转译require引用的js代码文件

### 常用options字段说明
env：指定在不同环境下使用的配置。比如production和development两个环境使用不同的配置，就可以通过这个字段来配置。env字段的从process.env.BABEL_ENV获取，如果BABEL_ENV不存在，则从process.env.NODE_ENV获取，如果NODE_ENV还是不存在，则取默认值"development"
plugins：要加载和使用的插件列表，插件名前的babel-plugin-可省略；plugin列表按从头到尾的顺序运行
presets：要加载和使用的preset列表，preset名前的babel-preset-可省略；presets列表的preset按从尾到头的逆序运行（为了兼容用户使用习惯）
同时设置了presets和plugins，那么plugins的先运行；每个preset和plugin都可以再配置自己的option

### 转译过程
babel的转译过程分为三个阶段：parsing、transforming、generating，以ES6代码转译为ES5代码为例，babel转译的具体过程如下：

ES6代码输入 ==》 babylon进行解析 ==》 得到AST（ 抽象语法树 Abstract Syntax Tree）
==》 plugin用babel-traverse对AST树进行遍历转译 ==》 得到新的AST树
==》 用babel-generator通过AST树生成ES5代码

[小编译器 es6-ast-es5](https://github.com/thejameskyle/the-super-tiny-compiler/blob/master/the-super-tiny-compiler.js)

### 命令行
转码结果输出到标准输出
$ babel example.js

转码结果写入一个文件
--out-file 或 -o 参数指定输出文件

$ babel example.js --out-file compiled.js

或者

$ babel example.js -o compiled.js


整个目录转码
--out-dir 或 -d 参数指定输出目录

$ babel src --out-dir lib

或者

$ babel src -d lib

-s 参数生成source map文件

$ babel src -d lib -s