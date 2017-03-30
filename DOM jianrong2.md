##2017年1月14日兼容性

标签（空格分隔）： 未分类

---

在此输入

 1. 如何检测一个方法浏览器是否支持；
     if( window.getComputedStyle){ 支持}else{不支持}
     window.getComputedStyle 
 检测全局变量或者函数的时候不要直接写名字；

2. demo.style.width 只能获取行间内的样式；
3. getComputedStyle（demo） 获取计算后的样式值（高版本）是全局的方法；
4. demo.getCurrentStyle获取计算后的样式值（低版本）是某个元素下的一个属性
5. 浏览器内核
    webkit 苹果，谷歌内核
    Gecko 火狐内核；
6.  firstChild 返回元素的第一个子节点 支持ie9以下低版本；
7.  firstElementChild 返回元素的第一个元素子节点；不支持ie9以下版本
8.  元素.childNodes 获取元素下所有子节点包括文本节点；标准的
9.  元素.chlidren 获取元素下所有元素子节点；非标准的
10.  window.pageYoffset; 滚动条向上滚动的距离 document.documentElement.scrollTop 在ie和火狐下document.body.scrollTop 在chrom下
11.  事件对象：通过事件对象得到当前这一事件的细节； 高版本浏览器中事件对象作为事件处理函数的第一个参数；低版本ie6、7、8中有一个全局变量event获取事件对象；
12.  element.addEventListener（evname，evFn，true|false）给元素绑定事件处理函数；里面的this指向触发事件的元素，高版本使用；
13.  element.attachEvent('on'+evname,evFn)里面的this指向window，需要用call把this指向触发事件的对象，只冒泡（ie低版本使用）
14.   element.detachEvent('click',fn);解绑attachEvent绑定的事件；
15.   mouseWheel滚轮事件 ie/chrome                     DOMMouseScroll火狐（必须用addEventListener绑定）
16.   onreadystatechange  兼容ie678  ajax每走一步都会触发这个函数，等到readyState等于4时请求完成；
ie低版本不支持onload，所以用readyState来监控是否请求完成； 
   在ie6下ajax对象用new ActiveXObject（'Microsoft.XMLHTTP')生成；


     






     
     





