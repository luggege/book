## CSS的部分兼容写法

##### 火狐与IE浏览器之间关于width的不同定义

CSS ’width’ 指的是标准CSS中所指的width的宽度，

* 在firefox中的宽度就是这个宽度。它只包含容器中内容的宽度。

* 而Internet Explorer ’width’则是指整个容器的宽度，包括内容，padding ，border。

* Firefox中：容器占的宽度=内容宽度+padding宽度+border宽度

* IE中：内容宽度=您定义的容器宽度\(Internet Explorer ’width’\)-padding宽度-border宽度 **所以，如果IE中定义 width:120px;padding:5px 的话，所显示的宽度就是120px.** 即padding:5px是在width里面。 而Firefox中，上面这个定义，显示宽度就是 130 px; 所以，我们就必须这样定义

 ```

 width:115px !important;width:120px;padding:5px;

 ```

 ### hack

 由于不同的浏览器，比如Internet Explorer 6,Internet Explorer 7,Mozilla Firefox等，对CSS的解析认识不一样，因此会导致生成的页面效果不一样，得不到我们所需要的页面效果。

 这个时候我们就需要针对不同的浏览器去写不同的CSS，让它能够同时兼容不同的浏览器，能在不同的浏览器中也能得到我们想要的页面效果。

 **这个针对不同的浏览器写不同的CSS code的过程，就叫CSS hack,也叫写CSS hack**

* !important这个规则对Ie6.0,Ie7.0和Firefox能写hack

* \*对于Ie系列浏览器都能够识别， firefox 浏览器则不能识别;

* !important只有Ie7.0和firefox可以识别，但是Ie6.0不能成功应用.

 * 1 区别ie与firefox的hack为:

 ```

 border:2px solid #f00;*border:1px solid #f00;

 ```

 * 2 区别Ie6.0 与Ie7.0、firefox的hack为:

 ```

 border:1px solid #f00!important;border:2px solid #f00;

 ```

* 在\(1\)中，之所以'\*'把放在后面是因为ff不识别,而导致只对它设置了一次border;而ie 系列进行了两次border设置后，后一个属性覆盖了前一个属性，故为一像素的边框。

* 在\(2\)中，之所以把!important放在第一个border 设置，是因为它把这次border的优先级提高了，即使后面在一次甚至在N次设置border 也无效，但是Ie6.0对这个规则不接受，而导致它应用了第二次的border 设置，也就是第二次覆盖了第一次的这一原理， 并不是它不识别!important;所以它的border为2 像素的红框.

#### 部分hack写法总结：

```

#box{

 color:red; //所有浏览器都支持

 color:red !important; //Firefox、IE7支持

 _color:red; //IE6支持

 *color:red; //IE6、IE7支持

 *+color:red; //IE7支持

 color:red \9; //IE6、IE7、IE8支持

 color:red \0; //IE8支持

}

```

## 网站如何同时兼容IE6、IE7、IE8

1. 第一招：**给常用CSS规定属性值。**body,div,dl,dt,dd,ol,h1,h2,h3,h4,h5,h6,form,input,p,th,td{margin:0;padding:0;}img{border:0px;}ul {margin:0px;padding:0px;}/ul li {list-style:none;}上面的建站常用代码就相是格式化CSS样式，让各浏览器按照我们设置的属性值渲染网页

2. 第二招：**IE和FF下对象居中问题**

 IE下大家应该知道只要设置

```

body{text-align:center;}

```

这样就可以居中显示。但是这样的方法在FF不行的。这里就需要给修改成

```

body:{text-align:center;margin:0px auto;}Margin

```

意思就是上下距离为0像素，左右为自动。所以FF就会居中显示。

3. 第三招：**垂直居中（仅只用于一行）**

 比如说一个高30px的div，默认是会显示在左上角，如果想垂直居中对其可以加个line-height:30px;样式。



 如果你想让他居下方则在修改line-height:30px;

数值越大越局下，为了防止撑破层，还需要再给一个样式overflow:hidden;(超出的部分不显示)

4. 第四招：**给每一个块对象设置三个样式**

```width:**px;height:**px;overflow:hidden;

```

即便高、宽是属性值是自动那么也需要去设置这三个样式。目的就是解决浏览器默认值的问题。

5. 第五招：**针对IE6、IE7、FF的css样式(这一招在特殊情况下经常用到)**

 原来建设网站经常使用!important来设置优先权，但有了IE7之后就不行了。

 下面给大家个可以解决IE6、IE7、FF各个CSS优先权的方法

 ** \#1 { color: #333; } FF环境**

 **\\\* html #1 { color: #666; } IE6环境 **

 **\\\*+html #1 { color: #999; } IE7环境**

 **上面的书写顺序一定不能去改变。**

 **这样子网页在FF下显示#333，IE6下显示#666，IE7下显示#999;**

#### -moz代表firefox浏览器私有属性

#### -ms代表IE浏览器私有属性

#### -webkit代表chrome、safari私有属性


