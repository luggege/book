### HTML5：HTML5 + CSS3技术

> HTML本来不会活过21世纪的。网页规范的制定者W3C组织，早在1998年就已经对HTML撒手不管了。W3C把未来都寄托在**XHTML**这个更具现代特色的后续规范上，XHTML被视为HTML的严肃整洁版，但XHTML举步维艰。当XHTML举步维艰的时候，有那么一群人\(来自欧朋\(OPera\)/火狐\(fireFox\)/苹果\(safari\)的一些具有开发者自行组建了WHATWG\(Web Hypertext Application Technology Working Group超文本应用技术工作组\)\)开始寻找新的解决方案，这就奠定了HTML5的的前身。
>
> **HTML5诞生于2004年**
>
> **HTML5的规范正式公布于2014年**

### 首先是HTML5的结构

* 文档类型声明

  ```js
  <!DOCTYPE HTML> //相比于html4除去了约束和版本号
  ```

* 字符编码

  ```js
  <meta charset="utf-8"> //声明字符集的编码
  ```

* HTML5的语法规则相比较HTML4更加松散

在开始H5的新特性之前先提一下**腻子脚本\(polyfill\)**以及**IE条件注释**

* IE条件注释功能是IE特有的一种功能，能对IE系列产品进行单独的XHTML代码处理，注意，主要是针对XHTML,而非CSS。条件注释功能非常强大，可以进行true和false判断。
* 主要是针对ie6 7 8对支持和让老浏览器支持html5+css3的一些js脚本

**所以这两个东西肯定都是为了兼容老版本的IE浏览器的**

语法如下：

lte：就是Less than or equal to的简写，也就是小于或等于的意思。

lt ：就是Less than的简写，也就是小于的意思。

gte：就是Greater than or equal to的简写，也就是大于或等于的意思。

gt ：就是Greater than的简写，也就是大于的意思。

! ：就是不等于的意思，跟javascript里的不等于判断符相同

```js
<!--[if IE]>
<![endif]-->

<!--[if lte IE 8]>
// 如果IE小于等于IE8
<script type="text/javascript" src="html5shiv.js"></script>
//引用的这个js就是一个比较好用的腻子脚本
<![endif]-->
```

### 然后下面开始是HTML5的新特性：

* 新的语义化标签
* * 当页面样式加载失败的时候能够让页面呈现出**清晰的结构**
  * 有利于**seo**优化，利于被搜索引擎收录（更便于搜索引擎的爬虫程序来识别）
  * 便于项目的**开发及维护**，使html代码更具有**可读性**，便于其他设备解析。

如下：

* * **Headerd** 定义section或page的页眉-----页面的头部
* * **Nav** 定义导航链接.一般定义导航
* * **main** 定义主要区域
* * **section** 定义文档中的节
* * **aside** 定义内容之外的内容，侧边栏
* * **footer** 定义section或者page的页脚
* 新的表单

* * **input 类型 -email邮箱类型**

```js
 <input type="email" name = "email" class = "email">;
```

* * **input 类型 -url 网址**

```js
<input type="url" name = "url" class = "url"></lable>;
```

* * **input 类型 -search 搜索框**

```js
<input type="search" name = "search" class = "search"></lable>t;
```

* * **input 类型 - number\(value,max,min,step\(数字的间隔\)\)**

```js
 <input type="number" name = "number" class = "number" min="0" max = "100" step = "2">
```

* * **input 类型 -range\(value,max,min,step\)滑块**

```js
<input type="range" name = "range" class = "range" min="2" max="100" step="2">
```

* * **Input 类型 - Date Pickers（time, date, month, week, datetime-local）**
* 多媒体（视频与音频）

* Canvas绘图

* 数据存储

* 离线应用

* 地理定位

* CSS3



