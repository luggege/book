# vue的安装及使用

### 安装

```bash
npm install vue
```

### 使用脚手架构建空项目

```javascript
npm install -g @vue/cli   //安装vue-cli3.0 版本(vue-cli 安装的是vue-cli2.X版本，想要更换版本，需卸载之前版本)
vue create myApp          //创建项目
```

使用vue-cli3.0版本创建的项目会将webpack配置文件隐藏，如果想要修改webpack中的配置，需在根目录下手动创建vue.config.js文件，具体配置见[https://cli.vuejs.org/zh/guide/webpack.html\#简单的配置方式](https://cli.vuejs.org/zh/guide/webpack.html#简单的配置方式%29%29%29\)

### 用法

```javascript
1. import Vue from 'vue'              //引入vue框架
2. import Element from 'element-ui'  //引入element-ui插件
3. Vue.use(Element)                  //使用element-ui插件，需在new Vue()启动应用之前完成
4. new Vue({})                       //创建vue实例
```

## 疑问

1. 什么情况需要挂载到vue实例上?

