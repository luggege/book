### oclazyLoay 按需加载

依赖文件:

> 1. angular.js
> 2. angular-ui-router.js
> 3. oclazyLoad.js

注入方式:

```js
angular.module('myApp', ['ui.router', 'oc.lazyLoad']);
```

使用方法

```js
  .state('account', {
        url: '/account',
        templateUrl: '../tpls/account.html',
        resolve: {
            deps: ['$ocLazyLoad', function( $ocLazyLoad ){
                return $ocLazyLoad.load([
                    '../css/account.css',
                    '../js/controllers/account.js'
                ]);
            }]
        }
    })
```

#### $uibModal 模态框使用

依赖文件

> 1. angular.js
> 2. angular-animate.js
> 3. ui-bootstrap-tpls.js

注入方式

```js
angular.module('myApp', ['ngAnimate', 'ui.bootstrap']);
```



