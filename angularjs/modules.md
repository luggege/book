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

```js
{"login":"登录","register":"注册"}
```

en.json 文件内容如下:

```js
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

* config 函数用 $translateProvider 服务配置 $translate 服务实现

```js
.config(['$translateProvider',function($translateProvider){

        // 获取所有cookie, 筛选lang对应的值(缓存中不存在设定语言时,首选浏览器默认语言)
        var lang = '';
        var cookieList = document.cookie.split('; ');
        angular.forEach(cookieList, function (item) {
            if( item.substring(0,item.indexOf('=')) === 'lang' ){
                lang = item.substring(item.indexOf('=') + 1);
            }
        });
        // 获取浏览器默认语言
        var defaultLang = (navigator.language || navigator.browserLanguage).toLowerCase();
        if( defaultLang === 'zh-cn' || defaultLang === 'zh' ){
            defaultLang = 'zh-cn';
        }else if( defaultLang === 'zh-tw' || defaultLang === 'zh-hk' ) {
            defaultLang = 'zh-hk';
        }else {
            defaultLang = 'en';
        }
        lang = lang || defaultLang;
        $translateProvider.preferredLanguage(lang); // 默认已注册的语言
        $translateProvider.useStaticFilesLoader({   // 选择加载何种本地国际化语言配置文件
            prefix: '/open/data/',                  // 指定文件前缀 (/open-api/data/en.json)
            suffix: '.json'                         // 指定文件后缀
        });

    }
])
```

* 使用方法（**$translate.use\(\)切换语言**）

```go
<select name="" id="" ng-model="currentLang" ng-options="lang.id as lang.name for lang in language" 
ng-change="switchLang()">
</select>
```

```js
  $scope.switchLang = function () {
    $translate.use($scope.currentLang);               //实现语言的切换
    $cookies.remove('lang');
    $cookies.put('lang', $scope.currentLang, {path: '/'});
    window.location.reload();
  }
```

。html页面使用内置的translate指令做国际化

```go
<p class="banner_con" ng-bind="'login' | translate"></p>
```

 。controller中注入$translate服务直接进行国际化服务

```js
$translate.instant('app.detail.refreshSuccess');
```

#### 代码高亮插件SyntaxHighlighter

#### angular-ui-router的使用

#### angular-ui-tree的使用

#### 

#### angular-ui-select的使用



