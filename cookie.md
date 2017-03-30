#cookie


标签（空格分隔）： 未分类

---

 1. 使用document.cookie设置cookie存在于会话阶段，如果把浏览器关了，cookie会自动清空；
 2. 如果让cookie在某个时刻清空，给这个cookie设置一个过期时间；
 3. document.cookie='ketang=2; expires= '
 4.
###localStorage 本地存储
浏览器可以对一个域下存5m大小的数据；
浏览器支持localstorage本地的，都提供一个localstorage对象；
localStorage.setItem(key,value);设置
localStorage.getItem(key);获取
localStorage.removeItem(key);删除
localStorage.clear();清除所有localStorage
对localStorage进行增删改的时候，会触发storage事件
在本页面中改变localStorage中的值 的时候，不触发storage事件，别的窗口打开的这个页面会触发storage事件；
//localStorage存储数据的方法
let storage = {
	save(key,value){//储存数据
		localStorage.setItem(key,JSON.stringify(value))
	},
	fetch(key){//获取数据
		return JSON.parse(localStorage.getItem(key)) || [];
	}
}
