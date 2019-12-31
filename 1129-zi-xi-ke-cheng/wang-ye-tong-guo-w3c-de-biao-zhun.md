# 网页通过W3C的标准

1. 万维网联盟（外语缩写：W3C）标准不是某**一个标准**，而是一系列标准的**集合**。网页主要由三部分组成：

* **结构\(Structure\)**
* **表现（Presentation）**
* **行为（Behavior）**

1. 对应的标准也分三方面：

* **结构化标准语言主要包括XHTML和XML**，
* **表现标准语言主要包括CSS**，
* **行为标准主要包括对象模型（如W3C DOM）、ECMAScript等**。

这些标准大部分由W3C起草和发布，也有一些是其他标准组织制订的标准，比如ECMA（European Computer Manufacturers Association）的ECMAScript标准。

## 网页通过W3C标准的步骤：

1. 图片的alt=""属性必须每张图片都加上,而且对齐属性用CSS来定义。不加不能通过XHTML1.0验证。
2. 每个文档必须加上DTD声明

```text
<!DOCTYPE html PUBLIC "-//W3C//DTDXHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
```

去掉后能通过验证，但有警告：No DOCTYPE found! Checking with default XHTML 1.0 Transitional Document Type。

1. RSS的XML通过时其中的域名地址必须与检测的地址一致,否则报错.
2. 标签的链接属性加上JAVASCRIPT事件时必须为\#空链,不能为javascript:;或javascript:void\(null\);
3. 同一个页面当中，同名的ID会产生冲突。所以以ID定义样式的必须改成类引用。

```text
<div id="a1">111</div> <div id="a1">222</div>
```

如果不用W3C来检测的话，在CSS设计里是允许这样做的。 那是程序的角度不能相同，CSS上是可以相同的! 之前就是相同的产生问题，后面就改成类引用了!\(简单的说就是id必须要是单一的不能重复 如果重复就使用class\)

1. 不可以省略双引号或者单引号
2. 标签之间不可错位嵌套。

```text
<div class="CaseDetaListSS">



原文链接：



<a href='/html/cases/cases_61.html'>



官方网站



</div>



</a>
```

不允许这样。

1. 所有标签必须都使用小写
2. FLASH的标签代码中不能含有,必须采用其它的方法实现。
3. 所有的标签中含有的属性必须有值\(官方的说法\)。
4. 标签必须配对完成,单标签必须以/关闭
5. JS和CSS外部引入文件必须加上类型定义:

```text
<script type="text/javascript"></script>



<style type='text/css'></style>
```

1. 所有的样式全部写在外部文件。用类名定义。在使用的地方引用。
2. 页面上的一些特殊字符必须用HTML代码来标识.如“&”写成“&“

\| 显示结果 \| 说明 \| Entity Name \| Entity Number \|

\| --- \| ------------- \|:-------------:\| -----:\|

\| \| 空格 \| `&nbsp;` \| `&#160;` \|

\| &lt; \| 小于 \| `&lt;` \| `&#60;` \|

\| &gt; \| 大于 \| `&gt;` \| `&#62;` \|

\| & \| &符号 \| `&amp;` \| `&#38;` \|

\| " \| 双引号 \| `&quot;` \| `&#34;` \|

\| x \| 乘号 \| `&times;` \| `&#215;` \|

\| ÷ \| 除号 \| `&divide;` \| `&#247;` \|

