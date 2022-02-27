# CSS

CSS 优先级：

* !important &gt; id &gt; class &gt; tag 
* 内联 &gt; 内部 &gt; 外部 （内部 &gt; 外部的前提还要看他们的层叠顺序，即外部引用在前）
* !important &gt; 内联

### border-radius 针对 table 失效

> 如果table设置了 border-collapse: collapse;\(边框可并\)样式时,border-radius就会无效. 除此之外可以应用到所有元素.
>
> 解决办法: 外边在套一层div

### border 针对tr无效

> 原因: td没有边框,把tr设的边框给覆盖掉了
>
> 解决办法: 给td设border,或给table设border

#### 画一条0.5px的线

* ```js
  // 1.scaleY
  transform: scaleY(0.5);
  transform-origin: 50% 100%; // 解决变虚的问题

  // 2.线性渐变 linear-gradient
  background: linear-gradient(0deg, #fff, #000);
  ```

### 使用如下meta标签使IE浏览器使用谷歌浏览器内核或最高版本的IE

> &lt;meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1"&gt;

## 使用媒体查询引入不同的CSS文件\(兼容不同屏幕\)

> &lt;link rel="stylesheet" type="text/css" media="screen and \(min-width: 479px\) and \(max-width: 639px\)" href="css/pic480.css"&gt;

## 如何解决IE8以下兼容html5标签

```js
<!-- 条件引入html5.js -->
<!--[if lt IE 9]>
<script src="js/html5.js"></script>
<![endif]-->
<!-- 条件引入线上html5文件 -->
<!--[if lt IE9]> -->
<script src="[http://cdn.bootcss.com/html5shiv/r29/html5.min.js](http://cdn.bootcss.com/html5shiv/r29/html5.min.js)"></script>
<![endif]-->
<!-- cdnjs -->
<!--[if lt IE 9]>
<script src="[https://cdnjs.cloudflare.com/ajax/libs/html5shiv/3.7.2/html5shiv.js](https://cdnjs.cloudflare.com/ajax/libs/html5shiv/3.7.2/html5shiv.js)"></script>  
<![endif]-->
```

> 但是如果ie6/7/8 禁用脚本的用户,那么就变成了无样式的"白板"网页,我们该怎么解决呢?  
> 我们可以参照facebook的做法，即引导用户进入带有noscript标识的 “/?\_fb\_noscript=1”页面，用 html4 标签替换 html5 标签，这要比为了保持兼容性而写大量 hack 的做法更轻便一些。
>
> &lt;!--\[if lte IE 8\]&gt;  
> &lt;noscript&gt;  
> &lt;style&gt;.html5-wrappers{display:none!important;}&lt;/style&gt;  
> &lt;div class="ie-noscript-warning"&gt;您的浏览器禁用了脚本，请 &lt;a href=""&gt;查看这里&lt;/a&gt; 来启用脚本!或者&lt;a href="/?noscript=1"&gt;继续访问&lt;/a&gt;.  
> &lt;/div&gt;  
> &lt;/noscript&gt;  
> &lt;!\[endif\]--&gt;

```js
// 在IE9以下的浏览器将创建h5标签,,但是要在css中将这些元素均设为**块级元素**,因为h5标签在低版本IE中默认为内联元素

<!--[if lt IE9]>
<script>

    (function() {
        if(!0) 
        return;

        var e = "abbr, article, aside, audio, canvas, datalist, details, dialog, eventsource, figure, footer, header, hgroup, mark, menu, meter, nav, output, progress, section, time, video".split(', ');

        var i= e.length;
        while(i--){
                document.createElement(e[i])
            }
        })()

</script>
<![endif]-->
```

## IE低版本兼容CSS3属性

> 解决方案: 使用 ie-css3.htc 文件
>
> 使用方法: 在要使用C3的元素样式中按以下方法引入: behavior: url\(ie-css3.htc\);

### 问题和必要的说明

> 毕竟不是浏览器自带的属性, 方法有一定局限性,注意事项如下:

1. 当前元素一定要有定位属性，像是position:relative或是position:absolute属性。
2. z-index值一定要比周围元素的要高，否则……只能说抱歉了~~

### 所支持的样式

1. border-radius
2. box-shadow
3. text-shadow

### IE中button的type属性默认值: button，其他浏览器默认type：submit

> IE10及以下input回车时，浏览器默认会执行页面中的第一个button的click事件，如要避免可将button标签改为input且type设为button类型，或者页面顶端写一个空的button标签且用父盒子包裹，父盒子宽高设为0将其隐藏。

## 利用C3限制div内文字字数

```css
overflow: hidden;
display: -webkit-box;
text-overflow: ellipsis; //文字隐藏后添加省略号
-webkit-line-clamp: 3; //控制行数
-webkit-box-orient: vertical; //子元素垂直排列
```

* 限制文字在一行内显示

```css
overflow: hidden; //溢出隐藏(指定宽度)
white-space: nowrap; //默认在不换行
text-overflow: ellipsis; //超出部分显示省略号
```

## 清除浮动遇到的问题

> overflow: hidden; 只适合子元素没有设置position的元素,,否则超出父盒子高的部分将被截掉

解决方法: 使用添加如下类的方法

```css
/*清除浮动*/
.clearfix:before, .clearfix:after{
  content: "";
  display: table;
}

.clearfix:after{
    clear: both;
}

.clearfix{
    *zoom: 1; /*IE/7/6*/
}
```

```css
/*清除浮动代码*/
.clearfix:after{   
    content:"";       
    display:block;
    clear:both;
    visibility:hidden;
    height:0
}    

.clearfix{
    zoom:1
}
```

#### white-space属性

| white-space属性 | 源码空格 | 源码换行 | &lt;br&gt;换行 | 容器边界换行 |
| :--- | :--- | :--- | :--- | :--- |
| normal | 合并 | 不换行 | 换行 | 换行 |
| nowrap | 合并 | 不换行 | 换行 | 不换行 |
| pre | 不合并 | 换行 | 换行 | 不换行 |
| pre-line | 合并 | 换行 | 换行 | 换行 |
| pre-wrap | 不合并 | 换行 | 换行 | 换行 |



