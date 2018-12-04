### 数字动画效果

1. 依赖**countUp.js**库  ` npm install countup.js  ===> countUp.js `
2. angularJs有封装好的指令  ` npm install countup.js-angular1 ===> `**`angular-countUp.js`**`（依赖countUp.js/angular.js文件）`
3. js中注入 **countUpModule  **模块，即可使用**countUp**指令\(调用countUp.js中的api，实现动画效果\)。
4. 如果需要监听滚动效果可引入基于angularjs的 **angular-scroll-spy **库，有**首次进入、每次进入、每次滚出**三种事件可监听，通过注入**scrollSpyModule**模块，自定义指令**scrollSpy，**指定唯一**id**

> ```js
> $scope.$on('elementFirstScrolledIntoView', function(event, dat) {
>   if(data === 'myElementId') {
>     //do something
>   }
> });
> ```

> ```html
> <i id="myElementId" count-up start-val="0" end-val="30" scroll-spy-event="elementFirstScrolledIntoView" scroll-spy></i>
> ```



1. 


