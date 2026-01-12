### nuxt简介

> 一种基于vue的应用框架，ssr服务端渲染，在服务端生成html返回给客户端，有利于SEO，首屏加载速度快，自动配置路由

### my-nuxt-app

> npx create-nuxt-app XXX

### Build Setup

```js
# install dependencies
$ npm install
# serve with hot reload at localhost:3000
$ npm run dev
# build for production and launch server
$ npm run build
$ npm run start
# generate static project
$ npm run generate
```

#### nuxt.js常见问题

* created生命周期会执行在客户端或服务端，而服务端是没有window、document这两个全局对象的，所以使用会导致服务报错甚至挂掉。

* * 没报错的原因：是ssr只在第一次刷页面的时候会用到服务端渲染，后续如果没有再次刷新，页面上的跳转都是通过router跳转的，这时就跟普通的vue一样，created只会执行在客户端，就不会报错，一旦刷新页面就会在服务端执行
* asyncData：运行在组件渲染之前\(服务端/路由变更前被调用\)，所以无法使用this。在服务端异步获取数据并生成页面。直接返回对象，无需在data中重复定义，合并到data中一并返回给当前组件，因此asyncData只能用于页面组件（pages文件夹下），不能用于自定义组件（components）

* axios中的http请求，既有服务端的也有客户端的，需要对异常情况做处理

```js
// 用户被禁用
if (res.data.code === 403) {
    if (process.server) { // 服务器
    app.res.clearCookie('token')
        app.res.clearCookie(getServerCookie(app.req.host) + 'token')
        app.redirect({
            path: '/disableUser'
        })
    } else { // 客户端
        setTimeout(() => {
            app.$delCookie('token')
            app.app.router.push({ path: '/disableUser' })
        }, 3000)
    }
}
```

#### server/ 目录

> 服务端运行的文件

#### nuxt.config.js

> nuxt.js的配置文件，只在服务端运行

#### asyncData 的参数（context）有哪些？

* app：app 对象
* store：存储，可以拿到store里的数据
* route：路由，可以拿到参数之类的
* params：url 路径参数，主要获取id
* query：可以理解为url上问号后面的参数
* env：运行环境
* isDev：是否是开发环境
* isHMR：是否是热更新
* redirect：重定向
* error：错误

* layouts/default.vue：默认布局

* layouts文件夹下自定义错误error.vue页面，当404或500的时候跳转

* assets文件下创建全局样式文件，在nuxt.config.js中配置全局common.css

* 全局：路由统一动效（约定好的类名：page-enter-active/page-enter）

* 单个文件：在全局样式里定义单独的过渡样式，然后在组件内设置类名

* ```js
  export default {
      // transition: '动画名'
      transition: 'test'
  }
  ```

#### 生命周期

nuxtserverInit

middleware: 配置\(onfig\)--》布局\(layout\)--》页面\(page\)

validate: 参数校验，校验失败，则自动跳转到错误页面

#### 路由

约定式：

展示区：&lt;nuxt /&gt;

* 声明式跳转：``<nuxt-link :to="{name: `goods-comment-uid`, params: {uid: 1}, query: {a: 1, b: 2}}">评论01</nuxt-link>``
* name：路由名目录名-其他目录-文件名（不带下划线）
* params: key 要对等文件名
* 子路由：目录代表子路由，子路由内部同级的文件，代表的是同一级路由

展示区层级控制

* pages/一级展示/二级展示
* / index.vue 会在一级展示
* / index.vue 空文档代表有默认页，不会寻找其他\_详情.vue

配置

**路由守卫：**

* 前置：依赖中间件middleware、插件
* * 全局守卫：nuxt.config 指向 middleware（redirect\(\)）
  * layouts 定义中间件
  * 组件独享守卫：
  * middleware
  * 插件全局前置守卫
* 后置：
* * 组件内部独享守卫：
  * 使用vue 的 beforeRouteLeave 钩子
  * 插件全局后置守卫

**数据交互**

> 安装：@nuxtjs/axios、@nuxtjs/proxy

* nuxt.config配置：
* ```js
  modules: [
      '@nuxtjs/axios'
  ]
  ```
* 跨域配置：

* ```js
  axios: {
      proxy: true, // 开启axios跨域
      prefix: '/api' // baseUrl
  },
  proxy: {
      '/api': {
          traget: 'http://localhost:3001', // 代理转发的地址
          changeOrigin: true,
          pathRewrite: {
              // '^/api': '' // 重替换
          }
      }
  }
  ```



