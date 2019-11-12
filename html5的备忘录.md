## HTML5的备忘录

##### HTML5是现在前端开发人员必备技能。

> HTML本来不会活过21世纪的。网页规范的制定者W3C组织，早在1998年就已经对HTML撒手不管了。W3C把未来都寄托在**XHTML**这个更具现代特色的后续规范上，XHTML被视为HTML的严肃整洁版，但XHTML举步维艰。当XHTML举步维艰的时候，有那么一群人\(来自欧朋\(OPera\)\/火狐\(fireFox\)\/苹果\(safari\)的一些具有开发者自行组建了WHATWG\(Web Hypertext Application Technology Working Group超文本应用技术工作组\)\)开始寻找新的解决方案，这就奠定了HTML5的的前身。

**HTML5诞生于2004年**

**HTML5的规范正式公布于2014年**

#### OK 我们开始吧

### 首先是HTML5的结构

* 文档类型声明

 ```

 <!DOCTYPE HTML> //相比于html4除去了约束和版本号

 ```

* 字符编码

 ```

 <meta charset="utf-8">//声明字符集的编码

 ```

* HTML5的语法规则相比较HTML4更加松散

* 总结：

 * 如何区分HTML和HTML5？

 **html5的文档声明去除了约束和版本号，html5的字符编码更加简洁**

 * DOCTYPE是什么？

 **DOCTYPE是文档类型声明**

 * HTML5有哪些新特性？

 **新增了语义化标签,多媒体,地理定位,离线存储,canvas**

#### 在开始H5的新特性之前先提一下腻子脚本(polyfill)以及IE版本条件注释

 * **IE条件注释功能是条件注释是IE特有的一种功能，能对IE系列产品进行单独的XHTML代码处理，注意，主要是针对XHTML,而非CSS。条件注释功能非常强大，可以进行true和false判断。**

 * **主要是针对ie6 7 8对支持和让老浏览器支持html5+css3的一些js脚本**

**所以这两个东西肯定都是为了兼容老版本的IE浏览器的**

语法如下：

lte：就是Less than or equal to的简写，也就是小于或等于的意思。

lt ：就是Less than的简写，也就是小于的意思。

gte：就是Greater than or equal to的简写，也就是大于或等于的意思。

gt ：就是Greater than的简写，也就是大于的意思。

! ：就是不等于的意思，跟javascript里的不等于判断符相同

```

<!--[if IE]>

<![endif]-->

<!--[if lte IE 8]>

 如果IE小于等于IE8

<script type="text/javascript" src="html5shiv.js"></script>

//引用的这个js就是一个比较好用的腻子脚本

<![endif]-->

```

### 然后下面开始是HTML5的新特性：

* 新的语义化标签

 * 语义化标签的含义？

 **答:通过标签就能明白标签中所包含的内容的这样的标签**

 * 使用语义化标签的好处

 1. **可以让文档更加清晰简洁**

 2. **可以让开发者更加容易修改和维护**

 3. **可以让索搜引擎和残障人士更好的获取网页信息**

* 新增了哪些语义化标签

 * 主要的：

 **Headerd** 定义section或page的页眉-----页面的头部

 **Nav** 定义导航链接.一般定义导航

 **main** 定义主要区域

 **section** 定义文档中的节

 **aside** 定义内容之外的内容，侧边栏

 **footer** 定义section或者page的页脚

 * 提问使用这些新的语义化标签跟我们之前使用div有什么区别？

 **为了被搜索引擎更好的检索**

 **为了浏览器实现特定功能（比如阅读功能）**

 **便于编程人员理解（即使是html5，光靠标签的语义也不够，还是要靠id、name甚至class的css命名来综合体现）**

 * 次要的：

 Article 定义文章

 Mark 定义有记号的文本

 Figure 定义媒介内容的分组,以及它们的标题

 figcaption 定义figure元素的标题

 details 定义元素的细节

 summary 定义可见的&lt;details&gt;元素标题

 progress 定义任何类型的任务的进度====&gt;进度条

* 新的表单

**input 类型 -email邮箱类型 **

```

 <lable>

 <input type="email" name = "email" class = "email">;

 </lable>;

```

**input 类型 -url 网址**

```

 <lable>

 <input type="url" name = "url" class = "url">;

 </lable>;

```

** input 类型 -search 搜索框**

```

 <lable>

 <input type="search" name = "search" class = "search">;

 </lable>t;

```

** input 类型 - number\(value,max,min,step\(数字的间隔\)\)**

```

 <lable>

 <input type="number" name = "number" class = "number" min="0" max = "100" step = "2">

 </lable>

```

** input 类型 -range\(value,max,min,step\)滑块**

```

 <lable>

 <input type="range" name = "range" class = "range" min="2" max="100" step="2">

 </lable>

```

**Input 类型 - Date Pickers（time, date, month, week, datetime-local）**

![](/assets/00.png)

![](/assets/11.png)

![](/assets/22.png)

![](/assets/33.png)

![](/assets/44.png)

![](/assets/66.png)

* 多媒体（视频与音频）

* Canvas绘图

* 数据存储

* 离线应用

* 地理定位

* 酷炫狂拽屌炸天的CSS特效


