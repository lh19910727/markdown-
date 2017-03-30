#**2017年1月9日回顾**


标签（空格分隔）：
1. js的组成
 2. 获取元素
 3. 绑定事件处理函数
 4. 变量
 5. 函数
 6. if判断
 7. for循环未分类




---

####**一** **、javaScript由三部分组成**
ECMAscript(javaScript核心标准)；
DOM（Document Object Model ）	文档对象模型
						DOM是关于创建，插入，修改，删除页面元素的标准；
						DOM赋予我们操作页面的能力。
BOM (Browser Object Model)浏览器对象模型	BOM是关于如何控制浏览器的一些东西，	目前BOM没有一个完整的标准。
####**二、获取元素的方式**
获取页面中元素的方式：
					id  ：  document.getElementById(id)
					class： (document || element).getElementsByClassName(className)
tagName： (document || element).getElementsByTagName(className)
selector：	(document ||element).querySelector(selector)  只获取第一个
querySelectorAll：	(document ||element).querySelectorAll(selector) 获取元素的时候，获取一个单一的元素 或者是一个类数组（集合）
####**三、绑定事件处理函数**

 1. 在事件触发的时候，做一些事情，写一个监听器（函数）来监听这个事件
 2. 绑定在事件上的函数叫 事件处理函数，事件监听器
 3. 以on开头的事件，绑定事件处理函数的时候，因为这个以on开头的事件作为元素的属性存在的，所有一个元素的同一个事件不能绑定多个事件处理函数
#### **四、变量**
作用：储存数据
好处：可复用、简化数据
语法：var变量名
命名规则：数字、字母、下划线、$符组合而成，不能以数字开头
命名风格：大小驼峰命名法；
####**五、函数**
函数：用来实现一定功能的程序(代码)块儿；
作用：复用代码；
返回值：返回值是根据return后面的值决定的 默认为undefined；
声明函数的语法：function 函数名(){
					//代码块
				}
命名规则：函数名的命名规则遵循变量的命名规则；
定义函数的两种方式：函数声明
					function fn(){}
					
					不能为匿名函数

				函数表达式
					var fn = function(){
	
					}
####**六、if判断**
#####**下面的条件是依次进行判断，如果一个条件一旦成立，不会继续看下面的条件是否成立**
if(条件){根据条件成立与否走这里的代码 条件成立则执行这里的代码}else{条件不成立执行这里的代码}
####**七、for循环**
语法：for(1，初始化,2，条件,3，语句){	/,4，循环体}
