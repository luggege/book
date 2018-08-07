### AngularJs基础用法及流程详解

#### angular.module\(\)参数说明

* **注册**一个模块

```JavaScript
var myApp = angular.module('myApp', [
        'ui.router',
        'oc.lazyLoad',
        'ngAnimate',
        'ngResource',
        'ngCookies',
        'ui.bootstrap',
        'ui.tree',
        'pascalprecht.translate'
    ]);

var myApp = angular.module('myApp',[]);
```

angular.module方法有两个参数：模板名称、依赖注入列表（为空则不需要依赖关系）。

* **获取**一个模板

```
var myApp = angular.module('myApp');
```

如果应用程序中已经有了这个模板，那么就返回和这个模板一样配置的模板；

如果应用程序中**不存在**，会抛出异常。

#### run方法及config方法

```js
myApp
    .run(
        ['$rootScope', '$state', '$stateParams',
            function ($rootScope, $state, $stateParams) {
                $rootScope.$state = $state;
                $rootScope.$stateParams = $stateParams;
            }
        ]
    )
```

```JavaScript
myApp
    .config(['$stateProvider', '$urlRouterProvider', '$ocLazyLoadProvider', '$locationProvider',
     function ($stateProvider, $urlRouterProvider, $ocLazyLoadProvider, $locationProvider) {
        $urlRouterProvider.otherwise('/account');
        $stateProvider
            // 概览
            .state('overview', {
                url: '/overview',
                templateUrl: '../tpls/overview.html'
                // resolve: {
                //     deps: ['$ocLazyLoad', function( $ocLazyLoad ){
                //         return $ocLazyLoad.load(
                //             'js/controllers/login.js'
                //         );
                //     }]
                // }
            })
```

run方法：最先执行的方法，在angular项目启动时只执行一次，用来定义全局的数据或逻辑

config方法：在模块加载阶段，对模块进行自定义配置

