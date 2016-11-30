###require读取文件
* 如果省略后缀,会按次序一次加载".js"/".node"/'.json'
** 尽量不要省略后缀 **

##规范

1. AMD===>sea.js
2. CMD===>require.js
3. common.js===>node.js

npm install -g 包名  全局安装就是安装命令行工具

###npm docs jquery
* 通过这个命令打开包相对应的文档

###npm config set prefix'路径' 修改全局安装目录(不建议)

###npm list 查看当前目录下安装的所有包

###package.json中的包名要和外边的文件夹名一致

** 把自己写的包放在npm官网上,才能install下载自己写的包 **


###npm i -S jquery@3.*  (npm install --save)
> 开发环境安装

###npm i -D jquery@3.* (npm install -save-dev)
> 生产环境安装

* 多个版本的jquery不会出现在同一个node_modules中
> 1.7.* 的版本名字叫做jQuery

### ~1.11.* 会下最小版本号的最新版 1.11.3

### ^1.11.* 会下中级版本号的最新版 1.12.4

##nrm数据源管理工具(npm install -g nrm)
* 切换数据源(nrm use taobao)===>.npmrc

###箭头函数
1. var foo=参数=>返回值

2. var foo=(参数1,参数2)=>返回值

3. var foo=参数=>{return v1 + v2}

4. var foo=()=>{console.log(v1)}


#脏检查
##MVVM
M: model  V: view  VM: ViewModel===>$scope

** 理解脏检查机制 **





















