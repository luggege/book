eslint

webpack

babel

用户状态管理

### 目录结构

```js
│  .browserslistrc                  // browser-loader 配置<br/>
│  .eslintrc.js                     // eslint-loader 配置<br/>
│  .gitignore                       // git 忽略项<br/>
│  babel.config.js                  // babel 配置项<br/>
│  jest.config.js                   // jest 配置项<br/>
│  package-lock.json                // package-lock.json<br/>
│  package.json                     // package.json<br/>
│  postcss.config.js                // postcss 配置项<br/>
│  vue.config.js                    // webpack配置项<br/>
├─dist                              // 打包后的生产环境目录，只需部署这个目录到生产环境<br/>
├─node_modules                      // 安装包<br/>
├─public                            // html模板<br/>
├─src                               // 源代码<br/>
│  ├─api                            // 所有请求<br/>
│      ├──login.js                  // 用户相关接口<br/>
│      ├──privilege.js              // 资源类接口<br/>
│      ├──enterpriseMember.js       // 企业用户接口<br/>
│  ├─assets                         // 图片等静态资源<br/>
│  ├─components                     // 全局公用组件<br/>
│  ├─icons                          // 项目所有 svg icons<br/>
│  ├─router                         // 全局路由管理<br/>
│  ├─store                          // store状态管理<br/>
│      ├──modules                   
│           ├──user.js              // 用户相关的状态<br/>
│      ├──getters.js                // store 的 state 中派生的一些状态<br/>
│      ├──index.js                  // 全局 vuex状态管理器<br/>
│  ├─styles                         // 全局样式<br/>
│      ├──base.scss                 // 基础样式表<br/>
│      ├──common.scss               // 公共样式表<br/>
│      ├──dialog.scss               // 公共弹框样式表<br/>
│      ├──sidebar.scss              // 公共侧边栏 主体布局样式表<br/>
│  ├─utils                          // 全局公用方法<br/>
│      ├──auth.js                   // 全局用户token的 增 删 改 查<br/>
│      ├──request.js                // axios请求封装<br/>
│  └─views                          // 所有模板页面<br/>
│  ├─App.vue                        // 入口页面<br/>
│  ├─main.js                        // 入口文件 加载组件 初始化等<br/>
│  └─permission.js                  // 权限管理<br/>
└─test                              // 打包后的测试环境目录，只需部署这个目录到测试环境<br/>
└─tests                             // 单元测试<br/>
```



