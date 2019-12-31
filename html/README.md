# 技术栈-sub插件安装及md语法

### 解决sublime package control 出现There are no packages available for installation

> 在 \([https://packagecontrol.io/installation\#st2\)下载](https://packagecontrol.io/installation#st2%29下载) Package Control.sublime-package 放到Sublime text 安装目录下的Packages 里面
>
> 参考博客: \([http://www.tuicool.com/articles/UBnYrq](http://www.tuicool.com/articles/UBnYrq%29%29\)

## 修改Sublime Text 3的侧边栏字体大小

1. **首先需要确保安装了Package Control**
2. **然后安装PackageResourceViewe**

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

