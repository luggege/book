### oclazyLoay 按需加载

1.依赖文件:

> 1. angular.js
> 2. angular-ui-router.js
> 3. oclazyLoad.js

2. 注入方式:

> angular.module\('myApp', \['ui.router', 'oc.lazyLoad'\]\);

3. 使用方法

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



