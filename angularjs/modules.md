### oclazyLoay 按需加载

* 依赖文件:

> 1. angular.js
> 2. angular-ui-router.js
> 3. oclazyLoad.js

* 注入方式:

```js
angular.module('myApp', ['ui.router', 'oc.lazyLoad']);
```

* 使用方法

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

* 依赖文件

> 1. angular.js
> 2. angular-animate.js
> 3. ui-bootstrap-tpls.js

* 注入方式

```js
angular.module('myApp', ['ngAnimate', 'ui.bootstrap']);
```

#### angular-cookies的使用

#### angular-autocomplete自动完成的使用

#### 

#### angular-translate国际化使用

angularjs作为前后端拆分的解决方案之一，当然离不开前端框架处理国际化的问题，angularjs官方出了一个模块--angular-translate来解决多语言国际化的问题。

* 依赖文件

> 1.angular.js
>
> 2.angular-translate
>
> 3.angular-translate-loader-static-files

angular-translate-loader-static-files是读取本地文件的模块，因为我们的翻译内容都是独立的json文件\(zh-cn.json、zh-tw.json、en.json\)。

zh-cn.json 文件内容如下:

```
{"login":"登录","register":"注册"}
```

en.json 文件内容如下:

```
{"login":"Login","register":"Register"}
```

上面2个json文件对应相同的键 ,我们称之为 **翻译键**.  不同的语言文件中,**相同的翻译键对应相应的翻译值**即可.如 "Login" 对应 "登录"

* 安装方法

```bash
bower install angular
bower install angular-translate
bower install angular-translate-loader-static-files
```

* 注入方式

```js
angular.module('myApp',['pascalprecht.translate']);
```

* 


#### 代码高亮插件SyntaxHighlighter

#### angular-ui-router的使用

#### angular-ui-tree的使用

#### 

#### angular-ui-select的使用



