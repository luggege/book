# Introduction

## 笔记

This flie is luwenxiu's note book .............

## Markdown的常用语法

标题

Markdown 标题支持两种形式：

> 1、用\#标记

在 标题开头 加上1~6个\#，依次代表一级标题、二级标题....六级标题 &lt;!-- more --&gt;

## 一级标题 <a id="&#x4E00;&#x7EA7;&#x6807;&#x9898;"></a>

### 二级标题 <a id="&#x4E8C;&#x7EA7;&#x6807;&#x9898;"></a>

#### 三级标题 <a id="&#x4E09;&#x7EA7;&#x6807;&#x9898;"></a>

**四级标题**

**五级标题**

**六级标题**

> 2、用=和-标记

在 标题底下 加上任意个=代表一级标题，-代表二级标题

## 一级标题 <a id="&#x4E00;&#x7EA7;&#x6807;&#x9898;-2"></a>

### 二级标题 <a id="&#x4E8C;&#x7EA7;&#x6807;&#x9898;-2"></a>

效果如下：

一级标题

二级标题

三级标题

四级标题

五级标题

六级标题

> 列表

### Markdown 支持有序列表和无序列表。 <a id="markdown-&#x652F;&#x6301;&#x6709;&#x5E8F;&#x5217;&#x8868;&#x548C;&#x65E0;&#x5E8F;&#x5217;&#x8868;"></a>

无序列表使用-、+和\*作为列表标记：

* Red
* Green
* Blue
* Red
* Green
* Blue
* Red
* Green
* Blue

有序列表则使用数字加英文句点.来表示：

1. Red
2. Green
3. Blue

### 引用 <a id="&#x5F15;&#x7528;"></a>

引用以&gt;来表示，引用中支持多级引用、标题、列表、代码块、分割线等常规语法。

常见的引用写法：

> 这是一段引用 //在`>`后面有 1 个空格
>
> ```text
> 这是引用的代码块形式    //在
> `
> >
> `后
> 面有 
> 5
>  个空格
> ```
>
> 代码例子：

```text
protected
void
onCreate
(Bundle savedInstanceState)
{

super
.onCreate(savedInstanceState);
    setContentView(R.layout.activity_main);
}
```

> 一级引用
>
> > 二级引用
> >
> > > 三级引用
>
> **这是一个四级标题**
>
> 1. 这是第一行列表项
> 2. 这是第二行列表项

### 强调 <a id="&#x5F3A;&#x8C03;"></a>

两个_或-代表加粗，一个_或-代表斜体，~~代表删除。

**加粗文本**或者**加粗文本**

_斜体文本_或者_斜体文本_

删除文本

### 图片与链接 <a id="&#x56FE;&#x7247;&#x4E0E;&#x94FE;&#x63A5;"></a>

图片与链接的语法很像，区别在一个 ! 号。二者格式：

图片：![&#x56FE;&#x7247;&#x6587;&#x672C;\(&#x53EF;&#x5FFD;&#x7565;\)](https://github.com/luggege/book/tree/f7d098fe1f889ccf3b383f621c0b48c599f5fdd3/图片地址)

链接：[链接文本](https://github.com/luggege/book/tree/f7d098fe1f889ccf3b383f621c0b48c599f5fdd3/链接地址/README.md)链接又分为行内式、参考式和 自动链接：

这是行内式链接：[ConnorLin's Blog](http://connorlin.github.io)。

这是参考式链接：[ConnorLin's Blog](http://connorlin.github.io/)，其中url为链接标记，可置于文中任意位置。

链接标记格式为：\[链接标记文本\]: 链接地址 链接title\(可忽略\)

这是自动链接：直接使用`<>`括起来[http://connorlin.github.io](http://connorlin.github.io)

这是图片：![](https://connorlin.github.io/images/avatar.jpg)

### 代码 <a id="&#x4EE3;&#x7801;"></a>

代码分为**行内代码**和**代码块**。

行内代码使用`代码`标识，可嵌入文字中 代码块使用4个空格或\`\`\`标识

```text
这里是代码
```

代码语法高亮在 \`\`\`后面加上空格和语言名称即可

```text
//注意语言前面有空格
这里是代码
```

例如：

这是行内代码`onCreate(Bundle savedInstanceState)`的例子。

这是代码块和语法高亮：

```text
// 注意java前面有空格
protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.activity_main);
}
```

### 表格 <a id="&#x8868;&#x683C;"></a>

表格对齐格式

居左：:---- 居中：:----:或----- 居右：----: 例子：

| 标题 | 标题 | 标题 |
| :--- | :--- | :--- |
| 居左测试文本 | 居中测试文本 | 居右测试文本 |
| 居左测试文本1 | 居中测试文本2 | 居右测试文本3 |
| 居左测试文本11 | 居中测试文本22 | 居右测试文本33 |
| 居左测试文本111 | 居中测试文本222 | 居右测试文本333 |

### 分隔线 <a id="&#x5206;&#x9694;&#x7EBF;"></a>

在一行中用三个以上的\*、-、\_来建立一个分隔线，行内不能有其他东西。也可以在符号间插入空格。

效果均为一条分割线

换行

在行尾添加两个空格加回车表示换行：

这是一行后面加两个空格 换行

### 脚注\(注解\) <a id="&#x811A;&#x6CE8;&#x6CE8;&#x89E3;"></a>

使用\[^\]来定义脚注：

这是一个脚注的例子[1](https://github.com/luggege/book/tree/f7d098fe1f889ccf3b383f621c0b48c599f5fdd3/这里是脚注/README.md)

### 常用弥补Markdown的Html标签 <a id="&#x5E38;&#x7528;&#x5F25;&#x8865;markdown&#x7684;html&#x6807;&#x7B7E;"></a>

### 字体 <a id="&#x5B57;&#x4F53;"></a>

&lt;font face="微软雅黑" color="red" size="6"&gt;字体及字体颜色和大小&lt;/font&gt;&lt;font color="\#0000ff"&gt;字体颜色&lt;/font&gt;

### 换行 <a id="&#x6362;&#x884C;"></a>

使用html标签`<br/>`&lt;br/&gt;换行

### 文本对齐方式 <a id="&#x6587;&#x672C;&#x5BF9;&#x9F50;&#x65B9;&#x5F0F;"></a>

&lt;p align="left"&gt;居左文本&lt;/p&gt;&lt;p align="center"&gt;居中文本&lt;/p&gt;&lt;p align="right"&gt;居右文本&lt;/p&gt;

### 下划线 <a id="&#x4E0B;&#x5212;&#x7EBF;"></a>

&lt;u&gt;下划线文本&lt;/u&gt;

