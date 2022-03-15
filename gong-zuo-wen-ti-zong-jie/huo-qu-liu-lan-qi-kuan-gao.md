### 浏览器相关问题

#### 获取浏览器宽高

```javascript
// 文档的宽 高（元素到顶端的距离）
console.log( document.body.scrollWidth );
console.log( document.body.scrollHeight || document.documentElement.scrollHeight );

console.log( $(document).width() );
console.log( $(document).height() );

// 文档滚动卷去的部分
console.log( document.body.scrollLeft );
console.log( document.body.scrollTop || document.documentElement.scrollTop );

// 总长度 - 卷去的 == 可视窗口的高度
console.log( document.body.scrollHeight - document.body.scrollTop );

console.log( document.body.clientWidth );
console.log( document.body.clientHeight || document.documentElement.clientHeight );

// 分辨率
console.log( window.screen.width );
console.log( window.screen.height );

// 当前窗口的可视区域的宽 高
console.log( $(window).width() );
console.log( $(window).height() );

div.style.top: 指对象距离浏览器显示区域顶端的垂直距离  (可读&可写 带单位)
div.offsetTop: 指对象距离顶边距显示区域顶端的垂直距离  (可读 不带单位)
```

```js
// 1.滑动到底部加载更多
window.onscroll = function(){
    //文档内容实际高度（包括超出视窗的溢出部分）
    var scrollHeight = Math.max(document.documentElement.scrollHeight, document.body.scrollHeight);
    //滚动条滚动距离
    var scrollTop = window.pageYOffset || document.documentElement.scrollTop || document.body.scrollTop;
    //窗口可视范围高度
    var clientHeight = window.innerHeight 
                        || Math.min(document.documentElement.clientHeight,document.body.clientHeight);

    if(clientHeight + scrollTop >= scrollHeight){
        console.log("===加载更多内容……===");
    }
}
```

```js
$(window).on("resize scroll", function(){
    var windowHeight = $(window).height();//当前窗口的高度
    var scrollTop = $(window).scrollTop();//当前滚动条从上往下滚动的距离
    var docHeight = $(document).height(); //当前文档的高度
    console.log(scrollTop, windowHeight, docHeight);
    //当 滚动条距底部的距离 + 滚动条滚动的距离 >= 文档的高度 - 窗口的高度
    //换句话说：（滚动条滚动的距离 + 窗口的高度 = 文档的高度） 这个是基本的公式
    if (scrollTop + windowHeight >= docHeight) {
        console.log("===加载更多数据===");
    }
});
```

```js
// 2.getBoundingClientRect：判断元素在视窗之内
rect = target.getBoundingClientRect();

rect.top >= 0 && rect.bottom <= viewHeight && rect.left >= 0 && rect.right <= viewWidth
```

```js
// 3.interSection observer：重叠观察者，
// 通过创建观察者，传入被观察者的方式，判断两个元素是否重叠，性能要比getBoundingClientRect好
const options = {
  // 表示重叠面积占被观察者的比例，从 0 - 1 取值，
  // 1 表示完全被包含
  threshold: 1.0, 
  root:document.querySelector('#scrollArea') // 必须是目标元素的父级元素
};

const observer = new IntersectionObserver(callback, options)

observer.observe(document.querySelector('#target'))
```

#### 页面位置

#### touch事件的属性

touchstart:当手指触摸屏幕时触发；即使已经有一个手指放在了屏幕上也会触发。

touchmove:当手指在屏幕上滑动时连续的触发。在这个事件发生期间，调用preventDefault\(\)可阻止滚动。

touchend:当手指从屏幕上移开时触发。

touchcancel:当系统停止跟踪触摸时触发。关于此事件的确切触发事件，文档中没有明确说明。

**以上事件的event对象上面都存在如下属性：**

touches:表示当前跟踪的触摸操作的Touch对象的数组。

targetTouches:特定于事件目标的Touch对象的数组。

changeTouches:表示自上次触摸以来发生了什么改变的Touch对象的数组。

**每个Touch对象包含下列属性：**

clientX:触摸目标在**视口**中的X坐标。

clientY:触摸目标在**视口**中的Y坐标。

identifier：表示触摸的唯一ID。

pageX：触摸目标在**页面**中的x坐标。

pageY：触摸目标在**页面**中的y坐标。

screenX:触摸目标在**屏幕**中的x坐标。

screenY:触摸目标在**屏幕**中的y坐标。

target:触摸的DOM节点坐标

#### 浏览器navigator属性

navigator 对象包含有关浏览器的信息。没有应用于 navigator 对象的公开标准，不过所有浏览器都支持该对象。但是其内部一些属性及其返回值在各浏览器并不统一。

* language：返回当前的浏览器语言（来自 Mozilla Developer Center）
* userLanguage：返回操作系统设定的自然语言（来自 MSDN）
* browserLanguage：返回当前的浏览器语言（来自 MSDN）
* systemLanguage：返回当前操作系统的缺省语言（来自 MSDN）

关于 navigator 对象的更多资料，请参见：[MSDN](http://msdn.microsoft.com/en-us/library/ms535867%28VS.85%29.aspx)、[Mozilla Developer Center](https://developer.mozilla.org/en/DOM/window.navigator)。

对于浏览器，Mozilla Developer Center 中的 language 属性与 MSDN 中的 browserLanguage 属性描述很像。

**代码中打印出了各浏览器对于这 4 个属性返回值的情况：**

|  | IE6 IE7 IE8 | Firefox Chrome Safari | Opera |
| :--- | :--- | :--- | :--- |
| navigator.language | undefined | zh-CN | zh-CN |
| navigator.userLanguage | zh-cn | undefined | zh-cn |
| navigator.browserLanguage | zh-cn | undefined | zh-cn |
| navigator.systemLanguage | zh-cn | undefined | undefined |

**解决方案**

可以使用下面的代码获取当前浏览器语言：

```javascript
(navigator.language || navigator.browserLanguage).toLowerCase()
```

```javascript
// 判断浏览器类型及版本
function getBrowserInfo(){
    var Sys = {};
    var userAgent = navigator.userAgent.toLowerCase();
    var reg =/(msie|firefox|chrome|opera|version).*?([\d.]+)/;
    var m = userAgent.match(reg);

    Sys.browser = m[1].replace(/version/, "'safari");
    Sys.version = m[2];
    return Sys;
}

//获取当前的浏览器信息
var system = getBrowserInfo();
```



