##2017年1月12日（ajax跨域）

标签（空格分隔）： 未分类

---

 1. **encodeURI**(str)把中文编码为uri格式
 2. **decodeURI**（）把uri格式解析为中文
 3. **onprogress**	监控下载进度
4.**enctype**: 当提交方式为post的时候，需要设置enctype，如果是在表单中，没有设置，默认是  application/x-www-form-urlencoded
    	作用：对数据进行编码，并通过请求头的方式告诉后端，发送的数据编码类型，方便后端接收到数据以后，进行对应的解码操作
    	1.application/x-www-form-urlencoded 默认 user=leo&
        2.multipart/form-data
        3.text/plain
        
        如果是get方式，传输的数据只有一种编码方式application/x-www-form-urlencoded
5.apache:
	路径： F:\wamp\bin\apache\Apache2.2.21\bin\php.ini
	post_max_size
	upload_max_filesize
6.new FormData()
data.append("file",oFile.files[0]);
xhr.upload.onprogress
7.所谓**同源**是指，域名，协议，端口相同
8.**域名**：
		域名就是ip地址的小名（外号）
		如果要域名和ip绑定，需要DNS解析
			主域名：https://www.baidu.com/
			二级域名：http://news.baidu.com/
			三级域名：http://29.classcase.sinaapp.com/
9.**协议**：不同服务器之间通信的一种约定
			http/https:访问互联网上的页面
			ftp
			file
			端口：
				http/https  80
				ftp  21 22 23
10.**跨域**：只要域名，协议，端口有一个不同就产生了跨域访问
11.使用 XMLHttpRequest和后台配合使用用的是PHP
		header("Access-Control-Allow-Origin:*");
12.**XDomainRequest**
通过代理的方式，跨域 后台的语言是不存在跨域的
13.可以跨域访问的标签：img、link、script
jsonp =>  json+padding  json格式填充数据；
14.**使用ajax跨域访问：**
					1. 在后端设置允许跨域
        						php为例 header("Access-Control-Allow-Origin:*");
        2. 代理方式	后端语言是不存在跨域的	              访问自己域下的后台文件，在后台文件中请求别的域上的数据
					3. flash
				4. jsonp
						后端设置jsonp请求数据的格式
15.**jsonp请求数据：**动态创建script标签，引入某一个文件，文件的内容会执行js代码，内容中会有一个函数执行，会全局的搜索这个函数，这个函数必须写全局函数
	在函数执行的时候传入数据，可以在函数中使用数据