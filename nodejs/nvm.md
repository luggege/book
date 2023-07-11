### nvm：管理nodeJs版本

> 用于解决包依赖不兼容，导致还原包报错，提示node版本过高或过低/当前某个包不兼容当前node，需要降低node版本或升级node版本

#### 安装nvm

```js
1. curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash
// 安装完 nvm 后切换源地址，命令：NVM_NODEJS_ORG_MIRROR=https://npm.taobao.org/mirrors/node
// 安装对应版本的 node
3、nvm install v14.7.0
// 设置node默认版本
nvm alias default v16.18.1
4、查看安装的node版本：nvm list
5、切换node版本：nvm use v版本号
```



