# 面试题

标签（空格分隔）： 面试题

---
1.
```
if (!("a" in window)) {
    var a = 1;
}
alert(a);=>undefined
```
2.
```
var a = 1,
    b = function a(x) {
        x && a(--x);
    };
alert(a);=>1
```
3.
```//如果函数名字和变量名字相同变量提升先提升变量在提升函数，函数覆盖变量
function a(x) {
    return x * 2;
}
var a;
alert(a);=》function a(x) {
    return x * 2;
}
```
4.
```
function b(x, y, a) {
    arguments[2] = 10;//
    alert(a);
}
b(1, 2, 3);
```
5.
```
function a() {
    alert(this);
}
a.call(null);=>window
```
参考地址：
[http://dmitry.baranovskiy.com/post/91403200](http://dmitry.baranovskiy.com/post/91403200)

1. 找出数字数组中最大的元素（使用Match.max函数）
Math.max.apply(this指向随意传，数组）
2. 转化一个数字数组为function数组（每个function都弹出相应的数字）
3. 给object数组进行排序（排序条件是每个元素对象的属性个数）
```
function Foo() {
    getName = function () { alert (1); };
    return this;
}
Foo.getName = function () { alert (2);};
Foo.prototype.getName = function () { alert (3);};
var getName = function () { alert (4);};
function getName() { alert (5);}

//请写出以下输出结果：
Foo.getName();=>2
getName();=>4
Foo().getName();=>1
getName();=>5
new Foo.getName();=》undefine
new Foo().getName();=>3
new new Foo().getName();
```




