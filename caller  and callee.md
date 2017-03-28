# caller 和callee的差别

标签（空格分隔）： 未分类

---

 - caller返回一个函数的引用，这个函数调用了当前的函数;callee返回正在执行的函数本身的引用，它是arguments的一个属性
- caller
caller返回一个函数的引用，这个函数调用了当前的函数。
使用这个属性要注意:
1 这个属性只有当函数在执行时才有用
2 如果在JavaScript程序中，函数是由顶层调用的，则返回null
functionName.caller: functionName是当前正在执行的函数。

- callee
callee返回正在执行的函数本身的引用，它是arguments的一个属性
使用callee时要注意:
1 这个属性只有在函数执行时才有效
2 它有一个length属性，可以用来获得形参的个数，因此可以用来比较形参和实参个数是否一致，即比较arguments.length是否等于arguments.callee.length
3 它可以用来递归匿名函数。


