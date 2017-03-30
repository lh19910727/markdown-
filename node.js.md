#node.js入口文件模板

标签（空格分隔）： 未分类

---
//先安装express模块，起服务的js文件放在一个目录下面
var express = require("express");
var app = express();
//设置文件的静态路径
app.use(express.static(__dirname+"/"));
//读取要加载的文件夹
app.get("/",function (req,res){
	res.sendFile(__dirname+"/iscoll-view/iscroll6.html");
})
//读取要加载的数据
app.get("/data",function (req,res){
	var arr = [];
	for( var i = 5; i < 300; i++ ){
		arr.push({
			"title":"title"+Math.floor(i*Math.random())+30
		})
	}
	res.json(arr);
})
//http://192.168.2.34:8888/手机端输入此链接就可以打开文件（手机要跟电脑处于同一网络下）
//监听服务器开启状态；（8888为端口号，192.168.2.34为本电脑的ipv4地址，输入ipconfig在命令板上可获取电脑的ipv4地址
app.listen(8888,"192.168.2.34",function(){
	console.log('启动服务成功');
})





