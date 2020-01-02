# 简历遇到的问题

1. 专业技能要体现到项目中
2. 用具体的模块来体现相关的技能点!
3. 利用面向对象封装过一些组件
4. AngularJs的一些指令\(ng-app,ng-moddle,ng-controller,ng-bind\)
5. 查各种调试工具
6. > 模块开发的演变 ==&gt;全局函数\(代码可读性差,没办法完整的写到一块使得全局变量增多\) ==&gt;命名空间\(牵强的解决命名冲突问题,不能解决私有性封装\)==&gt;划分私有空间\(实质是一个自调用函数,里边返回一个对象,其实命名还是需要来约定\)==&gt;扩展和维护模块\(遵循开闭原则: 对直接修改关闭,对扩展开放; 原理就是: 函数传参\(原来有就用原来的,么有就传一个空函数\)自调\)==&gt;第三方依赖\(SeaJs: 通过seajs.use\(路径,回调函数\)引入\)
   >
   > SeaJs遵循CMD规范,懒加载的方式加载模块, 通过\(启动模块 块\)seajs.use\(路径\)方法加载模块,
   >
   > 使用define\(function\(require, exports, module\){} \)方法定义模块;
   >
   > requireJs遵循AMD规范,优先加载, 主模块直接\( 使用 require\('add'\) \)加载模块add模块,另一子模块不需要define加载模 块;
7. Linux基本的命令有哪些\(rm:remove删除, cls:clean scrren清除屏幕, cd:change directory切换目录, md:make directory新建目录, ren:rename重命名, del: delete删除文件, dir:directory查看目录中条目\)
8. 脏检查机制: MVVM模型中,Angular内部的$watch会实时检查\(观察者模式,深度优先遍历\)$scope的值,当$scope的值发生变化时,就会触动$scope.$digest来将变化的值更新到视图中.手动设置.....也可将变化的值更新到视图中
9. 项目\(企业,学生是怎么实现注册的?\)具体是做什么的,有什么功能,负责什么模块\(主页,登录,注册\)
10. 项目展示模块是按什么分类的\(省份,行业\)
11. JS实现表单数据校验\(注册时候的 名字.密码的校验\)
12. H5C3有兼容问题,所以就不要在一起写处理过兼容问题\(避免冲突\)
13. 处理过主流浏览器问题\(不要写各种,可以写一下处理过哪个浏览器的那些兼容问题, 火狐,360....\)
14. H5C3具体实现的功能\(平移: translate, 缩放: scale, 翻转: rotate, 渐进渐出效果: 使用@frame动画0%到100%设translate从一个位置移动到另一个位置, 透明度设从全透明到不透明\)
15. 使用jQuery的ajax与后台交互\(原生的Ajax有兼容问题\)
16. zepto用来做交互的,不了解,不要写了.

    > zepto是针对移动端开发的库,是jQuery的轻量级替代品,jQuery的API它基本上都有,有一些基本的触摸事件可以用来做触摸屏交互,如: tap事件/swipe事件; 但是它不支持IE浏览器\(只是考虑到文件大小限制才不兼容的\),使用哪个模块就引入哪个模块,所以轻量\(zepto.js是基础模块;event.js事件模块==&gt;click\(\);fx.js动画模块==&gt;amimate\(\);touch.js移动端事件=&gt;swipeLeft\(\)\)
    >
    > zepto与jQuery的区别: zepto中没有为原型定义extend方法,而jQuery有; zepto的each 方法只能遍历数组,不能遍历json; zepto的width\(\)和height\(\)由盒模型\(box-sizing\)决定, 用.width\(\)返回赋值的width值,用.css\('width'\)返回的是包含padding和border的值,而jquery 会忽略盒模型,始终返回内容的宽高\(不包括padding和border\); zepto会阻止事件冒泡

17. table布局早就淘汰了,更不可能会出现在微信公众号中
18. canvas做统计用户数量的柱状图\(高是根据用户数量和底成比例画的图,用户使用数量数据是

    从后台取回来的,隔一段时间更新的\)

19. 代码优化具体体现在? \(代码复用性....\)
20. 活动页项目太简单,不要写
21. 技术点要用具体的模块来体现,可以夸大模块体现的技术点

reactjs,github,抓包工具,web app

 **position定位可以设置位移,c3中的transition也可以设置位移,但是transition是由浏览器内核直接渲染的.而position是先操作dom,然后在设置css样式,即先加载元素,计算位移之后在渲染,会减慢3-5倍的速度.** 
