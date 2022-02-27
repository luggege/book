# 屏幕适配

#### 浏览器默认字体大小16px,最小显示12px;

### 相对长度单位

1. em: 参照的是当前元素的字号 
2. rem: 参照的是html根元素的字号\(C3新增,IE9以上\),主要用在移动端 
3. vh: 相对于视口的高度。视口被均分为100单位的vh（若视口高度200，则8vh：8\*200/100）
4. vw: 相对于视口的宽度，同上
5. vmax相对于视口的宽度或高度中较大的那个

6. vmin：选取vw和vh中最小的那个

1. ```js
   html {
    font-size: 62.5%;
    /*10 ÷ 16 × 100% = 62.5%*/
   }
   body {
    font-size: 1.4rem;
    /*1.4 × 10px = 14px */
   }
   h1 {
    font-size: 2.4rem;
    /*2.4 × 10px = 24px*/
   }
   //在根元素中设置了一个百分比形式的基本字体大小,
   //这是因为浏览器默认字号是16px,用百分比定义了一个10px,只是为了下边使用rem单位的时候好计算;
   ```

   rem 的好处:

   * 可以等比例适配所有屏幕
   * 字体大小等可以等比例缩放,不会出现当浏览器改变页面大小的时候,字体不会跟随变化的尴尬问题
   * rem统一相对于根元素,避免了计算麻烦的问题

### 常见屏幕尺寸

> 320: iphone4/iphone5, 360: galaxy, 375: iphone6, 414: iphone6 plus

### 媒体查询,适配方案

**UI稿件640px/750px**

> 640px/20份 = 32px; \(16px 占0.5份\)
>
> 为了方便计算,不同屏幕下都分成20份

```js
@media only screen and (width: 320px) {
    html {
        font-size: 16px;
        // 每份的大小,如果原UI图给的是640px的,并且测的距离大小假如是16px,那么占其原来的0.5份,
        // 则在此适配屏幕下的距离大小就为: 0.5*16px=8px; 如果当前的单位是5rem,那么实际大小距离为: 16*5=80px;
    }
}

@media only screen and (width: 360px) {
    html {
        font-size: 18px;
    }
}

@media only screen and (width: 375px) {
    html {
        font-size: 18.75px;
    }
}

@media only screen and (width: 400px) {
    html {
        font-size: 20px;
    }
}

@media only screen and (width: 412px) {
    html {
        font-size: 20.6px;
    }
}

@media only screen and (width: 414px) {
    html {
        font-size: 20.7px;
    }
}
```

### 媒体查询

使用关键字only and not 链接媒体类型和媒体特性

#### 使用方法

1. link方法  \(media当做属性使用,相当于操作整个css文件\)
2. @media方法  \(写在style属性中\)

**device-width  检测设备宽度**

```js
//完全等于宽/高度时，才会变成蓝色
@media only screen and (width: 320px) and (height: 568px) {
    body {
        background-color: blue;
    }
}
```

```js
//小于等于宽/高度时，才会变成蓝色
@media only screen and (max-height: 400px) {
    body {
        background-color: blue;
    }
}
```

```js
//当视口中设置的width/height为device-height的值是,就会起作用
@media only screen and (device-height: 568px) {
    body {
        background-color: blue;
    }
}
```

> orientation: portrait \| landscape / _横/坚屏_ /

#### 屏幕默认宽度980像素

#### rem精简版实现自适应（flexible.js）

```js
//designWidth:设计稿的实际宽度值，需要根据实际设置
//maxWidth:制作稿的最大宽度值，需要根据实际设置
//这段js的最后面有两个参数记得要设置，一个为设计稿实际宽度，一个为制作稿最大宽度，例如设计稿为750，最大宽度为750，则为(750,750)
;(function(designWidth, maxWidth) {
    var doc = document,
    win = window,
    docEl = doc.documentElement,
    remStyle = document.createElement("style"),
    tid;

    function refreshRem() {
        var width = docEl.getBoundingClientRect().width;
        maxWidth = maxWidth || 540;
        width>maxWidth && (width=maxWidth);
        var rem = width * 100 / designWidth;
        remStyle.innerHTML = 'html{font-size:' + rem + 'px;}';
    }

    if (docEl.firstElementChild) {
        docEl.firstElementChild.appendChild(remStyle);
    } else {
        var wrap = doc.createElement("div");
        wrap.appendChild(remStyle);
        doc.write(wrap.innerHTML);
        wrap = null;
    }
    //要等 wiewport 设置好后才能执行 refreshRem，不然 refreshRem 会执行2次；
    refreshRem();

    win.addEventListener("resize", function() {
        clearTimeout(tid); //防止执行两次
        tid = setTimeout(refreshRem, 300);
    }, false);

    win.addEventListener("pageshow", function(e) {
        if (e.persisted) { // 浏览器后退的时候重新计算
            clearTimeout(tid);
            tid = setTimeout(refreshRem, 300);
        }
    }, false);

    if (doc.readyState === "complete") {
        doc.body.style.fontSize = "16px";
    } else {
        doc.addEventListener("DOMContentLoaded", function(e) {
            doc.body.style.fontSize = "16px";
        }, false);
    }
})(750, 750);
```

### css引入方式

1. html中,直接用link引less文件\(改rel="stylesheet/less"\)， 后缀只是告诉浏览器以哪种方式打开这个文件
2. 提供了一个@import可以引入外部less\(写在less中\)

> less: css预处理器的一种&lt;===&gt;sass
>
> less中除了可以@定义常量\(可参加运算\)外,也可以定义函数进行传参 好处: 结构清晰,便于维护,完全兼容css代码; 缺点: 需要编译

```js
.border(@r: 8px) {
    -webkit-border-radius: @r;
    -o-border-radius: @r;
    -moz-border-radius: @r;
    border-radius: @r;
}

header {
    .border(5px);
}

section {
    .border();
}
```

### 混合less写法

.mix\(\[形参\]: \[默认值\]\); 定义之后直接引用

#### 排除选择  .box:not\(要排除的选择器\){};



