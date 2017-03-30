# ECMAScript6

 1. 列表项

标签（空格分隔）： 未分类

---

在此输入正文

 1. let声明的变量只能在块级作用域中有效；
 2. let 声明的变量不会提升；
 3. let 声明的变量不会挂载window上；
 4. let 声明的变量不能再次被声明（不能使用let重复声明一个变量）；
 5. 暂存死区：从块的开始到声明这段的区域；
 6. 什么是块级作用域？一对{}包括的区域称为代码块。	**块级作用域**指一个变量或者函数只在该区域才起作用。
 7. 使用let关键字在代码块中声明的变量，只能在该代码块及子级作用域起作用。
 8. //每次循环的时候都会创建一个新的变量为i；
 //			for( let i = 0; i < allLi.length; i++ ){
//				allLi[i].onclick = function (){
//					alert(i);
//				};
//			}
 9. 常量：在定义之后值是不变的                   const+常量名（大写）  常量的值不可以修改，修改后会报错；（特性参考let声明的变量）
 10. 解构赋值：ES6允许按照一定模式，从数组和对象中提取值，对变量进行赋值，这被称为**解构**（Destructuring）。
**解构赋值的作用:**	函数只能返回一个值，如果要返回多个值，只能将它们放在数组或对象里返回。有了解构赋值，取出这些值就非常方便。
**eg1**:数组的解构赋值语法	var [a, b, c] = [1, 2, 3];
对象的解构赋值语法	var { foo, bar } = { foo: "aaa", bar: "bbb" };
**eg2**:function fn([username,age,sex="女"]){
				console.log( username,age,sex );
			}
			fn(["leo",29,"男"])
**eg3**:let obj = {
				userName:"leo",
				age:29,
				sex:"男"
			};								
let {userName:u,age,job:j="CEO"} = obj;  //起一个替代的名字
			console.log( u,age,j );
11.for of遍历的是value值；不能遍历没有遍历器（symbol.iterator)的对象;
**遍历器：**			它是一种接口，为各种不同的数据结构提供统一的访问机制。任何数据结构只要部署Iterator接口，就可以完成遍历操作（即依次处理该数据结构的所有成员）。
12.Object.keys(obj)快速得到对象的key值放入数组中；
13.**给对象添加遍历器**
Object.prototype[Symbol.iterator] = function (){
				var keys = Object.keys(this);  //得到对象的属性，放在数组中
				var index = 0;  //目的是依次取出keys
				var self = this;
				return {
					next:function (){
						return index < keys.length ? {
							value: self[keys[index++]],
							done:false
						} :
							{
							value: undefined,
							done:true
						}
					}
				}	
			};
14.arr.keys()用于for of对数组键名的遍历   语法：for(let index of arr.keys()){}
15.arr.entries() 用于for of对数组键值对的遍历  语法：for(let [index,ele] of arr.entries()){}
16.ES6允许字面量定义对象时，用方法二（表达式）作为对象的属性名，即把表达式放在方括号内。var obj = {
				a:1,
				["miaov"+1]:2,
				[abc]:3,
				["get"+1]:function (){
						
				},
				[o]:123   //key值都是字符串
			}
17.Object.is();用于对比参数是否严格相等，相对于===运算符，可以正确比较-0和0还有NaN
18.Object.assign()将source对象的可枚举属性赋值到target对象上。	注意：如果目标对象与源对象有同名属性，或多个源对象有同名属性，则后面的属性会覆盖前面的属性。只有浅复制，不能深度复制；
19.Object.getPrototypeOf(object) 用来获取一个对象的prototype对象；
20.Object.setPrototypeOf(obj,{say:function(){}})设置一个对象的prototype对象；
21，使用Object.defineProperty（obj,prop,descriptor） 定义属性，使用这个方法可以定义对象的描述
参数：obj 需要定义属性的对象
	prop 需定义或修改的属性的名字
	descriptor 将被定义或修改的属性的描述符
{数据描述
								value  该属性对应的值
								writable 是否可以被重赋值  默认为false 不能赋值
								enumerable 是否可以被枚举  默认为false 不能被枚举
								configurable 是否允许再次描述，是否允许删除 默认false 不允许再次对属性描述和删除
							}
22.描述属性的时候两种方式：**数据描述**和**存取描述**
{存取描述
								get(){}
								set(){}
								enumerable
								configurable
							}
						
23.//给参数设置默认值
			//定义默认值的参数必须是尾参数，因为定义默认值之后该参数可忽略。
24.**rest参数**
					用于获取函数的参数 或多余的参数 放在数组中（注意：rest后边不能再有其他参数，否则会报错）
25.函数中一旦使用了**es6**的语法，默认都是严格模式；使用"use strict"开启严格模式会报错
26.扩展运算符（spread）是三个点（...）。它好比rest参数的逆运算,将一个数组转为用逗号分隔的参数序列。
var arr = [1,2,3];
			var arr2 = [4,5,6];
			//var newArr = arr.concat(arr2);==>
			var newArr = [...arr,...arr2]
27.**箭头函数**
					ES6允许使用“箭头”（=>）定义函数
var f = n => n+1;
			//以上相当于：
			var f = function(n){return n+1;	}
//箭头函数中，在定义的时候就确定this的值
箭头函数不能当做构造函数，否则会报错
 11. set 数据结构，类似数组，但是成员值都是唯一的没有重复的项；new set（）
eg：var arr = [1,2,3];
var arr2 = [2,3,4,5];把两个数组合并成一个数组并去重；
var newArr = [...new Set([...arr,...arr2])];
 12. Set数据结构 new Set();  添加成员set.add() Set是一个构造函数，可以传入一个数组初始化默认值
 13. set.size 
					Set的实例的成员个数（数组的长度）
				set.add(value)
					为Set的实例添加值，返回值是新的对象
				set.delete(value)
					删除Set实例的值,返回值是布尔值
				set.has(value)
					判断传入的参数是否为set的成员，返回布尔值
				set.clear()
					清除set中所有成员，返回值undefined
 14. new Promise:ES6的Promise对象是一个构造函数，用来生成Promise实例。下面是Promise对象的基本用法。
 15. 所谓**Promise对象**，就是代表了未来某个将要发生的事件（通常是一个异步操作）。它的好处在于，有了Promise对象，就可以将异步操作以同步操作的流程表达出来，避免了层层嵌套的回调函数
三种状态：
						Pending（进行中）、
						Resolved（已完成，又称Fulfilled）
						Rejected（已失败）
 16. fetch(input, init).then(function(response) { ... });

				
		