
##ajax（原生）

标签（空格分隔）： 未分类

---

 1. AJAX是一种创建动态网页的技术；
 2. 可实现局部更新；
 3. form表单
 method:提交方式方法；（get，post）
action：提交地址
        get：可以缓存历史记录；数据放在？后面格式以key=value                 key=value&key=value （key值是前端和后端约定好的，代表一个有意义的属性）
         1.因为浏览器缓存地址，所以不安全
            2.浏览器对地址栏中的字符有限制，所以如果get的数据超出了             浏览器对地址的字符限制，那么会导致发送的数据不完整
        post：隐藏‘？’后面的地址（相对安全）
        理论上不限制大小，服务器那边限制大小；
####注意：post可以提交多种格式的数据，设置一个请求头，告诉后端发送的是什么样的格式的数据
xhr.setRequestHeader("Content-Type",'application/x-www-form-urlencoded');
###ajax请求过程：
 1. 通过构造函数得到ajax对象 XMLHttpRequest
 2. 链接地址,准备数据
 3. 发送数据
 4. 后端传输数据（不一定相应完成）
 5. 传输数据完成
 xhr.open（）=>xhr.onload()=>xhr.send()
####onreadystatechange : ajax每一步的状态；
###open：
参数：1.请求的方式
            2.请求地址
            3.布尔值（是否为异步，true为异步，false为同步）
            异步：不必等一件事做完先执行另一事；
            同步：等一件事做完再执行另一件事；
decodeURI:解码

----------
