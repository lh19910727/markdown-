# 严格模式



标签（空格分隔）： 未分类

---
**开启严格模式**：
       * 1. 在一对script标签的开始使用字符串 "use strict"
       * 2. 在函数中使用字符串 'use strict'
       
 1. use script严格模式下
 2. 严格模式下 delate 删除对象上的属性，不能删除全局变量；删除全局变量会报错；
 3. argument在正常模式下不是关键字也不是保留字，但是在严格模式下会报错；严格模式下arguments不再追踪参数的变化；
 4. 对象不能有重名的属性，函数不能有重名的参数；
 5.函数表达式的函数名字，只能在函数内部使用
 4. 在if判断里面，for循环里面，不能进行函数声明，会报错；
 5. 函数必须声明在顶层或者函数内部；
 6. 1.let声明的变量只能在所声明的块级作用域内有效；2.let声明的变量不会提升；3.let声明的变量不会挂在window上 ；4.let声明的变量不能够重复声明会报错；5.暂存死区：从快的开始到声明这段的区域；
 7. 常量：const+常量名 常量的值不能被改变；常量的名字全部大写；特性参考let声明的变量；
 
#大纲版
*
       * 严格模式 "strict mode"
       *
       * 使用严格模式可以消除js语法上不合理，不严谨，减少怪异的行为
       *
       * 开启严格模式：
       * 1. 在一对script标签的开始使用字符串 "use strict"
       * 2. 在函数中使用字符串 'use strict'
       *
       * 在严格模式下，使用以下的注意点：
       *
       * 1. 直接调用函数，函数中的this就不指向window了，而是undefined
       * 2. 使用call第一参数改变this指向，在es5中指向是window，在严格模式下执行传入的第一个参数
       * 3. 形参不能重复声明，重复声明会报错
       * 4. arguments不能追踪变化
       * 5. 不允许对arguments赋值
       * 5. 声明变量必须显式的使用var来声明变量，不是用var回报错
       * 6. 试图用delete删除变量会报错
       * 7. 函数声明必须在顶层或函数作用域中，在非函数的代码块中会报错
       *
       * 参考：http://www.ruanyifeng.com/blog/2013/01/javascript_strict_mode.html
       * https://developer.mozilla.org/en-US/docs/JavaScript/Reference/Functions_and_function_scope/Strict_mode





