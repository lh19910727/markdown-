# node讲解大纲


##初级部分讲解内容

 - 简介nodejs
 - REPL交互式解析器
 - 模块系统
 - process全局对象
 - Buffer对象
 - fs文件操作模块
 - Net模块
 - Http模块
 - Url模块
 - 案例：简易留言本

---


# 简介nodejs

Node.js 是一个基于 Chrome V8 引擎的 JavaScript 运行环境。Node.js 使用了一个事件驱动、非阻塞式 I/O 的模型，使其轻量又高效。Node.js 的包管理器 npm，是全球最大的开源库生态系统。

基于ECMAScript扩展的语言，内置扩展了如：文件系统、网络、操作系统、系统进程线程、HTTP等等模块，我们还可以通过安装第三方的模块来操作数据库、邮件、图片等等。

备注：可简略的说一下nodejs的事件驱动原理和非阻塞式 I/O 的模型是怎么一回事，只要往深的说学员能够明白，可以自由发挥。

# REPL交互式解析器

REPL(Read Eval Print Loop:交互式解释器) 表示一个电脑的环境，类似 Window 系统的终端或 Unix/Linux shell，我们可以在终端中输入命令，并接收系统的响应。

node自带的交互解析器，可以执行以下任务：

读取 - 读取用户输入，解析输入的Javascript
执行 - 执行输入的语句
打印 - 输出结果
循环 - 循环操作以上步骤
解析器运行：

在nodejs安装目录，打开node.exe执行程序，会出现一个黑色的框框，这个就是node提供用来解析js的解析器。

在黑色框框中输入js代码1+2,立马就会的出现结果3，打印出结果后，还可以继续输入语句。

解析器读取输入的语句，执行语句后打印出结果，然后继续在重复以上步骤，这么一个过程。

备注：可以在解析器中多输入多条js语句，用来说明写的js代码被解析

解析器常用的命令:

.help - 列出使用命令
.break - 退出多行表达式
.clear - 退出多行表达式
.exit - ctrl+d
.save filename - 保存当前的 Node REPL 会话到指定文件
.load filename - 载入当前 Node REPL 会话的文件内容

ctrl + c：.break
ctrl + c (两次)：.exit
ctrl + d：.exit  
向上/向下 键 - 查看输入的历史命令
tab 键 - .help
运行文件

在实际的开发中，通常是把js写在js文件中，然后执行这个文件得到结果。创建js文件，在解析器中运行.load 文件路径运行文件得到结果。

window系统终端

除了node提供的解析器解析js外，也可以使用系统提供的终端（演示使用window的终端）。

打开终端，输入node并回车，就进入了REPL交互模式；输入node 文件路径用来运行js文件。

例子：

创建js文件hello.js，输入代码：

console.log("hello,nodejs!");
利用终端运行，使用命令node hello.js

备注：一个小技巧：window系统在文件目录按shift键，然后右击，会出现“在此处打开命令窗口”，用来打开终端

#模块系统

实际的项目中，开发过程中会有多个文件，每个文件被划分不同的功能，例如有些文件是用来判断数据类型的函数集，也有文件是ajax请求，这样每个功能会写在不同文件中，使用的时候需要引入文件才能使用。

在node中，为了更好组织、管理代码，nodejs引入了模块。一个文件就是一个独立的模块。

模块的使用

先建两个文件，一个是入口文件inde.js,一个是工具文件tools.js。 
在tools.js文件中，写入工具函数:

function add(a,b){
    return a*b;
}
function isFunction(param){
    return typeof param === 'function';
}
在index.js中使用tools.js中的工具函数，需要tools.js这个模块对外暴露接口。

对外暴露接口

当一个模块被创建的时候，自动会有一些模块下的变量（对象、方法），比如：require()，module对象，exports对象。其中的module对象保存提供了该模块的一些信息。如果想把当前模块中的数据对外进行提供（暴露）接口，需要使用module对象下的exports对象，我们只要把需要对外提供的数据挂载到该对象下面就可以了。那么通过require方法加载了一个模块以后，这个方法会返回被加载模块的module.exprots对象。

有一个全局的exports对象，其实指向的就是module.exports对象。 
使用全局对象exports挂载属性向外暴露接口。

exports = add;
exports = isFunction;
有时只对外暴露一个对象，也可以使用module.exports，格式： 
module.exports = add;

不能同时使用exports和module.exports，否则后者会代替前者。

模块的加载

在index.js，这样使用：

var add  = require("./tools.js");
console.log(add);
使用require来加载所需要的模块。

如果tools.js使用的是exports暴露的接口，则add是一个对象;

如果tools.js使用的是module.exports暴露的接口，则add是module.exports对应的值

作用域

每个模块都有自己的独立作用域 - 模块作用域

梳理一下目前学习的作用域:

全局作用域
函数作用域
块作用域（ES2015+）
模块作用域
在浏览器运行时候，有一个全局对象为window，在node中全局对象为global。

一个模块就有独立的作用域，因此使用var声明的变量不会挂载在global上，如果不使用var声明，会挂载在global上，挂载在global上的属性，任何模块都可以访问，访问全局的变量可以省略global。除了自己定义的属性，global上还有其他的全局对象供开发者使用。

模块分类

核心模块 - Core Modules
文件模块 - File Modules
目录模块 - Folder Modules
核心模块： 
核心模块是node提供的模块，存放在node源码lib目录中，无需定义可直接加载使用比如http、fs、url等，核心模块加载只需要添加模块名称即可。 
文件模块： 
每一个文件都是一个模块，使用exports或module.exports对外暴露接口即可。文件模块的加载必须是（相对或绝对的路径），就算要加载的模块在当前目录下，也需要加路径./ 
目录模块： 
以某种约定格式存在在指定文件夹下的模块，通常放在node_modules文件夹下。 
在目录模块中需要有一个package.json文件，基本的格式为： 
{ 
"name": "", 模块名字 
"version": "",模块版本 
"main": ""模块入口文件 
}
模块加载路径

不同类型的模块加载方式是有区别的

核心模块和目录模块加载不需要添加路径
文件模块的加载一定需要显示的写出路径
备注：加载自定义的非系统模块如果在当前目录下，不可以省略 ./ 路径

例如：在当前文件下有一个文件为app.js,同一个目录下需要加载这个模块则需要带上./：

var app = require("./app.js");
# process全局对象

process是global下的属性，是一个全局变量，在任何一个地方都可以访问。process是描述运行时进程状态的对象，提供了当前程序信息的相关操作。

查看node运行进程

每当node运行一个文件时候，都会在后台程序开启一个进程。

先创建一个文件为index.js,在文件中写上一个定时器，目的是让程序一直运行，而不至于运行完之后就立马退出。

var n = 0;
setInterval(function (){
    n++;
    console.log(n); 
},1000)
当使用命令node index.js运行后，命令行一直打印数字。

打开操作系统的任务管理器，可以在后台进程中看到正在运行的node进程。使用ctrl+c后，停止运行，进程随之退出。

process.exit()退出当前进程

当n的值加到5时，调用process.exit()退出进程。

var n = 0;
setInterval(function (){
    n++;
    if(n === 5){
        process.exit(); 
    }
},1000)
process.argv获取命令行参数列表

在运行文件时候，可以向当前进程传入参数，以空格隔开

在文件时index.js，写入:

console.log(process.argv),
使用命令行运行node index.js a b=1,可得到一个数组，数组中存放的是命令行参数列表：

[<path>/node, <path>/index.js, a, b=1]
数组前两项是node的安装路径和运行文件的路径，后面的是以空格分隔的参数。

标准输入输出流

运行一个程序，不可避免的需要输入输出操作，也即I/O操作。node通过全局对象process提供方法完成输入输出行为。

标准输入流是从标准输入设备（键盘）流向程序的数据
标准输出流是从程序流向标准输出设备（屏幕）的数据
输入设备包括键盘、鼠标、手写板、扫描仪等 
输出设备包括显示器、打印机、扬声器、磁盘或光盘等

流：数据流。

标准输入输出流：按照一定的标准，从输入设备输入数据，经过运算之后，从输出设备输出数据显示。

Process.stdout标准输出流对象

在运行过程中，输出数据，使用Process.stdout下的方法：

Process.stdout.write(data <,charset> <,callback>)
其实console.log()输出数据，内部就是使用Process.stdout.write实现：

console.log = (msg) => {
  process.stdout.write(`${msg}\n`);
};
Process.stdin标准输入流对象

向运行程序输入数据，则先开启标准输入流，调用Process.openStdin()函数。这时候运行文件，就不会立马运行完成，而是会让输入数据。

通过Process.stdin.on('data', function(chunk){})，监听输入流的data事件，当输入回车的时候触发该事件，但注意chunk为接收到的数据块，默认为Buffer数据。需要把Buffer数据转成字符串，调用toString()方法。

# Buffer对象

Buffer对象是提供的全局对象，使用Buffer对象更好的操作二进制数据。

+





