# 前端模块化进程

标签（空格分隔）： 未分类


javascript

原始写法

模块就是实现特定功能的一组方法。只要把不同的函数简单地放在一起，就算是一个模块。 
最早开始是这样写代码的：

//util.js
function m1(){
    //代码
}
function m2(){
    //代码
}
常常会将一些通用的、底层的功能抽象出来，独立成一个个函数。使用的时候，只需要把util.js文件引入就可以使用。

这样写法的缺点：“污染”了全局变量，容易命名冲突。

命名空间（Namespace）模式

把模块写成一个对象，所有成员都放在对象中。 
虽然这样减少了全局变量，但也有显著的缺点：

可改写模块状态（不安全）
命名空间过长
暴露了缺点对应的也有解决方案：

立即执行函数（IIFE）
沙箱模式（Sandbox）
可改写模块状态

//util.js
var util = {
    initVal:0,
    m1:function(){
        //代码
    },
    m2:function(){
        //代码
    }
}
只需要这样调用：

util.m1();
这样的写法会暴露所有模块成员，内部状态可以被外部改写。

util.initVal = 1000;
改写了initVal的值，其他函数中使用initVal就会不正确。 
这个问题可以使用立即执行函数解决。

立即执行函数（IIFE）

使用"立即执行函数"（Immediately-Invoked Function Expression，IIFE），可以达到不暴露私有成员的目的。

var util = (function(){
    var initVal = 0;
    function m1(){
        //代码
    }
    function m1(){
        //代码
    }
    return {
        m1:m1.
        m2:m2
    }
})()
这样写就把initVal变成了私有变量，外面访问不到，无法被改写。

命名空间过长

在多人团队中开发，命名空间依然可能冲突，为了继续降低冲突概率，只好拉长命名空间。 
下面这段代码节选自 Yahoo! 的一个开源项目：

if (org.cometd.Utils.isString(response)) {
    return org.cometd.JSON.fromJSON(response);
}
if (org.cometd.Utils.isArray(response)) {
    return response;
}
为了避免冲突用了那么长一个命名空间，对记忆和书写的负担实在太重了。 
这个问题Yahoo的一个开源框架YUI，使用的是沙箱模式解决了这个问题。

沙箱模式

YUI使用了这种模式，很好的解决了命名过长的副作用：

YUI().use('node', function (Y) {
  // Node 模块已加载好
  // 下面可以通过 Y 来调用
  var foo = Y.one('#foo');
});
国内类似的框架KISSY也是这样的实现：

//定义模块
KISSY.add('custom',function(S){
        return {
            m1:123
        };    
    });
//使用模块
KISSY.use(["node","custom"],function(s,node,custom){
    console.log(s,node)
});
把要用到的模块加载进来，然后就可以使用。

在前端开发过程中，命名冲突和文件依赖是两个很经典的问题。以上只是解决了命名冲突。还有依赖的问题依然存在。

依赖

依赖util开发一个通用的弹框组件，给其他人使用，在使用的使用要先引入util库。

<script src="util.js"></script>
<script src="dialog.js"></script>
<script>
 new Dialog();
  // 代码！
</script>
这样引入可以正常使用，但使用的人多了难免会出现以下的引入方式，忘了引入util这个库。

<script src="dialog.js"></script>
<script>
 new Dialog();
  // 代码！
</script>
这样引入就会出现报错。引入util文件，就正常了。 
这样看似解决了这个问题，在后续开发中还有别的问题：

当要升级dialog组件库，用到了XXX.js文件，则其他使用dialog文件的页面都需要引入XXX.js。页面很多，只能手动引入。
去掉了dialog组件中部分功能，不再使用util文件，把页面中的util文件全部去掉，发现还有报错，部分人在其他项目中使用了util中的函数。 
.....
以上很多问题都是因为文件依赖没有很好的管理起来。在前端页面里，大部分脚本的依赖目前依旧是通过人肉的方式保证。当团队比较小时，这不会有什么问题。当团队越来越大，公司业务越来越复杂后，依赖问题如果不解决，就会成为大问题。

在css中一个样式文件依赖另一个，可以使用import引入：

@import url("base.css");
#test {...}
.classA {...}
.classB {...}
只用一个 @import 就解决了，页面中引入 css 时，只需要引入这个 css ，浏览器会自动去下载 base.css。css 文件的依赖能够实现自动管理，而不是像 js 一样，需要手动地去编写。

那使用js文件，处理依赖的时候，能不能像css那样，那个文件依赖另一个文件，文件中使用一种特殊的方式引入就可以呢？答案是：可以的。

模块的规范

有了模块，就可以更方便地使用别人的代码，想要什么功能，就加载什么模块。这样做有一个前提，那就是大家必须以同样的方式编写模块，否则每个人都有不同的写法，并且互不兼容，岂不是乱了套。

在Es6中制定了Moudle规范，受到了js不能读取本地文件的限制，在浏览器端还无法使用。借助node的一些工具可以使用。
目前模块化的两大规范:

CommonJs 同步加载模块规范
AMD/CMD 异步加载模块规范
CommonJs规范主要使用在node服务端。 
AMD/CMD使用在Web浏览器端。

定义模块遵循了CommonJs的规范，就可以在服务端和浏览器端共用模块

Web浏览器端的模块加载器

一个文件就是一个模块，在浏览器端使用模块加载器，使用到了那个文件模块，在一个文件中加载指定的模块。

模块加载器 
模块加载器就是一个功能库，比较知名的有两个，并且这两个工作方式有点区别：

requirejs 
遵循的是AMD(Asynchronous Module Definition)规范 
意思就是"异步模块定义"。它采用异步方式加载模块，模块的加载不影响它后面语句的运行。所有依赖这个模块的语句，都定义在一个回调函数中，等到加载完成之后，这个回调函数才会运行。
seajs 
遵循的是CMD(Common Module Definition)规范
定义模块 
定义模块

requirejs 使用define(id?, dependencies?, factory); 
seajs 使用define(function(require,exports,moudel){ 
//exports、moudel对外暴露接口 
});
使用模块

requirejs 使用 require([module], callback); // 依赖前置，提前执行 
seajs 使用 require(callback);// 依赖就近，延迟执行
node服务端模块加载

2009年，美国程序员Ryan Dahl创造了node.js项目，将javascript语言用于服务器端编程。 
这标志"Javascript模块化编程"正式诞生。

在nodejs中加载模块，使用全局函数require，

require(模块)
暴露模块接口,使用全局的exports或moudel.exports 
两者的区别：

module.exports 初始值为一个空对象 {} 
exports 是指向的 module.exports 的引用 
require() 返回的是 module.exports 而不是 exports
Es6中模块

一个文件就是一个模块，暴露文件中的功能，使用export

// math.js 
export default math = { 
PI: 3.14, 
foo: function(){} 
}
在文件使用import from引入

// app.js 
import math from "./math"; 
math.PI
但是以上浏览器为了安全考虑，限制了js读取文件，所以在浏览器短暂是无法使用，借助node服务端的工具可以使用。

export语法

export default {};
// export Declaration
export function foo(){
    console.log('I am not bar.');
}
// export VariableStatement;
export var PI = 3.14;
export var bar = foo;   // function expression
// export { ExportsList }
var PI = 3.14;
var foo = function(){};
export { PI, foo };
import语法

// import { ImportsList } from "module-name"
import { PI } from "./math";
import { PI, foo } from "module-name";
// import IdentifierName as ImportedBinding
import { foo as bar } from "./math";
bar();  // use alias bar
// import NameSpaceImport
import * as math from "./math";
math.PI
math.foo()
打包

在浏览器端使用模块加载器，本质上还是会请求多个js文件，这就导致HTTP请求过多。需要把多个文件合并压缩为一个js代码，减少HTTP请求，有利于优化。

参考链接

Why SeaJS

JavaScript 模块化历程

Javascript模块化编程（一）：模块的写法

Javascript模块化编程（二）：AMD规范

Javascript模块化编程（三）：require.js的用法

前端模块化开发的价值

前端模块化开发那点历史

JavaScript 模块化七日谈





