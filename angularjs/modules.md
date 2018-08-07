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

#### angular-cookies的使用

#### angular-autocomplete自动完成的使用

#### 

#### angular-translate国际化使用

angularjs作为前后端拆分的解决方案之一，当然离不开前端框架处理国际化的问题，angularjs官方出了一个模块--angular-translate来解决多语言国际化的问题。

1.依赖文件

> 1.angular.js
>
> 2.angular-translate
>
> 3.angular-translate-loader-static-files

2.





#### 代码高亮插件SyntaxHighlighter

#### angular-ui-router的使用

#### angular-ui-tree的使用

#### 

#### angular-ui-select的使用



