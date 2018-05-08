### oclazyLoay 按需加载

依赖文件:

> 1. angular.js
> 2. angular-ui-router.js
> 3. oclazyLoad.js

注入方式:

> angular.module\('myApp', \['ui.router', 'oc.lazyLoad'\]\);

使用方法

```
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



