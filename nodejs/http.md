# http

1. localhost: 不走网卡
2. 127.0.0.1: 走网卡
3. 192.168.141.xx: 先对外发送给路由或者是交换机,染回再找到自己的ip地址

## request和response的使用

## querystring核心模块

> 格式化字符串==&gt;json对象

## url模块的使用

## 使用http模块开发一个简单的网站

## 两种通过命令调用js的方式

> 原本执行的时候是通过node这个运行环境来直接运行1.js的,而现在可以

1. 通过创建出来的package.json,在scripts对象中添加"test": "node 1.js" ,就可以直接通过node环境来输入命令 npm test就可以运行1.js了;
2. 在创建出来的package.json中,创建bin对象 "bin":{"hehe": 1.js},在node环境下输入npm link安装完模块\(node\_modules\)之后,在全局变量中直接输入命令 hehe 就可以运行1.js了

