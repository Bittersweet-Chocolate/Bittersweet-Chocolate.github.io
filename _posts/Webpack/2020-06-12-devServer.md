---
layout:     post
title:      devServer
subtitle:   重要的知识点
date:       2020-06-12
author:     BY czh
header-img: img/webpack.png
catalog: true
tags:
    - webpack
    - devServer
---

###  devServer

>版本：webpack 4.42.1

安装方式：npm i webapck-dev-server -D

配置

* package.json

	```
	    "scripts":{
	        dev:"webpack -dev-server"
	    }
	```
* webpack.config.js

	```
		// 服务器配置
	    devServer:{
	    	open: true,	//自行打开浏览
	    	host: "localhost",	//指定服务ip
	    	port: 8080,	//启动端口号
	    	hot: true,	//启动热替换
	    	openPage: '/different/page',	//打开指定url的网面
	    	proxy:{
	    		// 反向代理 匹配url路径
	    		'/api':{
	    			//	根据参数进行拦截讲请求地址替换为 如下：
	    			target: 'https://www.aa.com',
	    			ws: true, //允许代理 websockets 协议
        			changeOrigin: true //需要虚拟托管的站点要设计为true
	    		}
	    	}	
	    }
	    
	```


