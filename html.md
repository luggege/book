### 解决sublime package control 出现There are no packages available for installation

> 在 \([https://packagecontrol.io/installation\#st2\)下载](https://packagecontrol.io/installation#st2%29下载) Package Control.sublime-package 放到Sublime text 安装目录下的Packages 里面
>
> 参考博客: \([http://www.tuicool.com/articles/UBnYrq](http://www.tuicool.com/articles/UBnYrq%29%29\)

# 修改Sublime Text 3的侧边栏字体大小

1. ### 首先需要确保安装了Package Control
2. ### 然后安装PackageResourceViewe

> 快捷键`⌘(command)+⇧(shift)+P`打开 Command Palette  
> 输入`Package Control:Install`回车，等待加载package列表  
> 搜索并安装`PackageResourceViewer`包

### 3.最后，使用PackageResourceViewer打开Theme文件进行编辑

> 快捷键`⌘(command)+⇧(shift)+P`打开 Command Palette  
> 输入`PackageResourceViewer: Open Resource`回车，打开包列表  
> 选择`Theme - Default`，再选择Soda Dark 3.sublime-theme \(首选项--用户中查看自己的主题找到对应的配置文件\)  
> 搜索`sidebar_label`，在`"class": "sidebar_label"`后边加一行：`"font.size": 18`，将字体大小设置为18，保存。
>
> 搜索sidebar\_tree，在"row\_padding": \[8, 8\],修改后边的数字，改变行距

# Markdown的常用语法

标题

Markdown 标题支持两种形式：

> 1、用\#标记

在 标题开头 加上1~6个\#，依次代表一级标题、二级标题....六级标题 &lt;!-- more --&gt;

# 一级标题 {#一级标题}

## 二级标题 {#二级标题}

### 三级标题 {#三级标题}

##### 四级标题 {#四级标题}

###### 五级标题 {#五级标题}

###### 六级标题 {#六级标题}

> 2、用=和-标记

在 标题底下 加上任意个=代表一级标题，-代表二级标题

# 一级标题 {#一级标题-2}

## 二级标题 {#二级标题-2}

效果如下：

一级标题

二级标题

三级标题

四级标题

五级标题

六级标题

> 列表

## Markdown 支持有序列表和无序列表。 {#markdown-支持有序列表和无序列表}

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

## 引用 {#引用}

引用以&gt;来表示，引用中支持多级引用、标题、列表、代码块、分割线等常规语法。

常见的引用写法：

> 这是一段引用 //在`>`后面有 1 个空格
>
>     这是引用的代码块形式    //在
>     `
>     >
>     `后
>     面有 
>     5
>      个空格
>
> 代码例子：

```
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
> #### 这是一个四级标题 {#这是一个四级标题}
>
> 1. 这是第一行列表项
> 2. 这是第二行列表项

## 强调 {#强调}

两个_或-代表加粗，一个_或-代表斜体，~~代表删除。

**加粗文本**或者**加粗文本**

_斜体文本_或者_斜体文本_

删除文本

## 图片与链接 {#图片与链接}

图片与链接的语法很像，区别在一个 ! 号。二者格式：

图片：![](图片地址 "图片文本\(可忽略\)")

链接：[链接文本](链接地址)链接又分为行内式、参考式和 自动链接：

这是行内式链接：[ConnorLin's Blog](http://connorlin.github.io)。

这是参考式链接：[ConnorLin's Blog](http://connorlin.github.io/)，其中url为链接标记，可置于文中任意位置。

链接标记格式为：\[链接标记文本\]: 链接地址 链接title\(可忽略\)

这是自动链接：直接使用`<>`括起来[http://connorlin.github.io](http://connorlin.github.io)

这是图片：![](https://connorlin.github.io/images/avatar.jpg)

## 代码 {#代码}

代码分为**行内代码**和**代码块**。

行内代码使用`代码`标识，可嵌入文字中 代码块使用4个空格或\`\`\`标识

```
这里是代码
```

代码语法高亮在 \`\`\`后面加上空格和语言名称即可

```
//注意语言前面有空格
这里是代码
```

例如：

这是行内代码`onCreate(Bundle savedInstanceState)`的例子。

这是代码块和语法高亮：

```
// 注意java前面有空格
protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.activity_main);
}
```

## 表格 {#表格}

表格对齐格式

居左：:---- 居中：:----:或----- 居右：----: 例子：

| 标题 | 标题 | 标题 |
| :--- | :--- | :--- |
| 居左测试文本 | 居中测试文本 | 居右测试文本 |
| 居左测试文本1 | 居中测试文本2 | 居右测试文本3 |
| 居左测试文本11 | 居中测试文本22 | 居右测试文本33 |
| 居左测试文本111 | 居中测试文本222 | 居右测试文本333 |

## 分隔线 {#分隔线}

在一行中用三个以上的\*、-、\_来建立一个分隔线，行内不能有其他东西。也可以在符号间插入空格。

---

---

---

---

效果均为一条分割线

换行

在行尾添加两个空格加回车表示换行：

这是一行后面加两个空格 换行

## 脚注\(注解\) {#脚注注解}

使用\[^\]来定义脚注：

这是一个脚注的例子[1](这里是脚注)

## 常用弥补Markdown的Html标签 {#常用弥补markdown的html标签}

## 字体 {#字体}

&lt;font face="微软雅黑" color="red" size="6"&gt;字体及字体颜色和大小&lt;/font&gt;&lt;font color="\#0000ff"&gt;字体颜色&lt;/font&gt;

## 换行 {#换行}

使用html标签`<br/>`&lt;br/&gt;换行

## 文本对齐方式 {#文本对齐方式}

&lt;p align="left"&gt;居左文本&lt;/p&gt;&lt;p align="center"&gt;居中文本&lt;/p&gt;&lt;p align="right"&gt;居右文本&lt;/p&gt;

## 下划线 {#下划线}

&lt;u&gt;下划线文本&lt;/u&gt;

