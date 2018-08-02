## 获取浏览器宽高

```
// 文档的宽 高
console.log( document.body.clientWidth );

console.log( document.body.clientHeight );

console.log( $(document).width() );

console.log( $(document).height() );


// 文档滚动卷去的部分
console.log( document.body.scrollLeft );

console.log( document.body.scrollTop );


// 总长度 - 卷去的 == 可视窗口的高度
console.log( document.body.clientHeight - document.body.scrollTop );


// 分辨率
console.log( window.screen.width );

console.log( window.screen.height );


// 当前窗口的可视区域的宽 高
console.log( $(window).width() );

console.log( $(window).height() );


div.style.top : 指对象距离浏览器显示区域顶端的垂直距离  (可读&可写 带单位)
div.offsetTop : 指对象距离顶边距显示区域顶端的垂直距离  (可读 不带单位)
```

### 页面位置 {#页面位置}

### touch事件的属性 {#touch事件的属性}

touchstart:当手指触摸屏幕时触发；即使已经有一个手指放在了屏幕上也会触发。

touchmove:当手指在屏幕上滑动时连续的触发。在这个事件发生期间，调用preventDefault\(\)可阻止滚动。

touchend:当手指从屏幕上移开时触发。

touchcancel:当系统停止跟踪触摸时触发。关于此事件的确切触发事件，文档中没有明确说明。

#### 以上事件的event对象上面都存在如下属性： {#以上事件的event对象上面都存在如下属性}

touches:表示当前跟踪的触摸操作的Touch对象的数组。

targetTouches:特定于事件目标的Touch对象的数组。

changeTouches:表示自上次触摸以来发生了什么改变的Touch对象的数组。

#### 每个Touch对象包含下列属性： {#每个touch对象包含下列属性}

clientX:触摸目标在**视口**中的X坐标。

clientY:触摸目标在**视口**中的Y坐标。

identifier：表示触摸的唯一ID。

pageX：触摸目标在**页面**中的x坐标。

pageY：触摸目标在**页面**中的y坐标。

screenX:触摸目标在**屏幕**中的x坐标。

screenY:触摸目标在**屏幕**中的y坐标。

target:触摸的DOM节点坐标



## 浏览器navigator属性



