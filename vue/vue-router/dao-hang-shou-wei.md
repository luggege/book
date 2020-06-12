### 导航守卫

> 导航：表示**路由**正在发生改变，利用导航守卫控制导航跳转

```js
// import router from './router'
import store from './store'
import {getToken} from './utils/auth'   //getToken from cookie

import Vue from 'vue'
import Router from 'vue-router'
Vue.use(Router)

const router = new Router({
  routes: constantRouterMap
})

router.beforeEach((to, from, next) => {
  console.log(to, from);

  // determine if there has token
  if( getToken() ){
    // has token
    if( to.path === '/login' ){
      next()
    }else {
      // 判断当前用户是否已拉取完user_info信息
      if( store.getters.roles.length === 0 ){
        store.dispatch('GetUserInfo').then(() => { // 拉取user_info
          /**
           * roles: [
           *      internalUser            普通用户（内部用户）
           *      administrator           超级管理员（内部用户）
           *      lawfirmUser             律所用户
           *      notarialOfficeUser      公证处用户
           * ]
           */
          const roles = store.getters.roles

          store.dispatch('GenerateRoutes', { roles }).then(() => { // 根据roles权限生成可访问的路由表
            router.addRoutes(store.getters.addRouters) // 动态添加可访问路由表
            next({ ...to, replace: true }) // hack方法 确保addRoutes已完成 ,set the replace: true so the navigation will not leave a history record
          })
          // }).catch((err) => {
          // store.dispatch('FedLogOut').then(() => {
          //    // Message.error(err || 'Verification failed, please login again')
          //     next({ path: '/' })
          // })
        })
      } else {
        next()
      }
    }
  }else {
    // has no token
    if( to.path === '/login' ){
      next()
    }else {
      next(`/login?redirect=${to.path}`)
    }
  }
})
```

```js
beforeEach主要有3个参数to，from，next：
to：route即将进入的目标路由对象，
from：route当前导航正要离开的路由
next：function一定要调用该方法resolve这个钩子。执行效果依赖next方法的调用参数。可以控制网页的跳转。

to: {
    name: "user"
    meta: {__ob__: Observer}
    path: "/user"
    hash: ""
    query: {}
    params: {}
    fullPath: "/user"
    matched: (2) [{…}, {…}]
    redirectedFrom: "/"
    __proto__: Object
}

from: {
    name: null
    meta: {}
    path: "/"
    hash: ""
    query: {}
    params: {}
    fullPath: "/"
    matched: []
    __proto__: Object
}
```



