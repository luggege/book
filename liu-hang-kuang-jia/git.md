# Git

## shell分类

* 图形界面shell
* 命令行shell

## bash属于shell

Linux默认使用bash

### 常见bash命令

**格式:** 命令 \[-option\] 参数

* pwd\(Print Woking Directory\) 查看当前目录
* ls\(List\) 查看当前目录下内容\(详细内容可加可选项 -a\(all\) \)
* cd\(Change Directory\) 切换目录到...
* mkdir\(Make Directory\) 创建目录
* touch 创建文件
* rm\(remove\) 删除文件
* rmdir\(remove Directory\) 删除目录
* cat 查看文件全部内容
* head -n 5\(-5\) 查看文件前5行
* tail 查看文件后几行
* cp\(copy\) 复制文件
* mv\(move\) 移动文件或重命名
* tab 自动补全
* history查看历史操作
* &gt; 和 &gt;&gt; 重定向\(&gt;覆盖 &gt;&gt;追加\)
* whoami 查看当前用户
* wget 下载
* tar 解压缩
* curl 网络请求

## vi 编辑器

### 三种模式

**打开/创建文件 vi + 文件路径**

* 命令模式
* 输入模式\(编辑模式\)
* 底行模式\(末行模式\)
* 命令模式: i o O a A ===&gt; 输入模式

  dd: 删除当前行

  yy: 复制当前行

  p: 黏贴内容

  u: 撤销回上一步

  ZZ: 保存并退出

  ctrl+f: 向前翻页

  ctrl+b: 向后翻页

* 底行模式: w: 保存 q: 退出 wq: 保存退出 q!: 不保存强制退出 e!: 撤销更改,返回上一次保存的状态 set nu: 设置行号\(esc退出\)

## 远程登录

> 除了登录自己电脑之外的所有服务器都叫远程登录

* 使用ssh登录 SSH是一种网络服务协议

## 版本控制

* 本地版本控制系统
* 集中版本控制系统
* 分布式版本控制系统

### Git工作原理

1. 工作目录
2. 暂缓区域
3. Git仓库

* git config 初始化配置
* git init 初始化仓库
* git clone 克隆仓库
* git add 给缓存增添东西\( -A添加全部\)
* git commit -m '备注信息'\(放到仓库中的编号\)
* git status 查看仓库当前文件状态\(红色未提交,绿色已提交\)
* git log 查看历史
* git checkout 切换到其他分支下

> git checkout SHA -- "某个文件"，代表只是从SHA这个版中取出特定的文件，

* git reset --hard 工作区会变 暂缓区会变 历史会变
* git reset --soft 只改变历史
* git reset --mixed\(默认\) 工作区不会变, 历史改变, 暂存区改变
* git checkout 只是取出特定的文件,不会改变历史

**git reset和git checkout是有区别的: git reset 会重写历史,git checkout 不会**

### 更新本地仓库为远程仓库

 **git fetch 远程仓库地址**   **git fetch 远程仓库地址 分支名称**

### git fetch 和 git pull区别

* git fetch 只是更新到本地仓库,代码不会体现到相应的工作目录中,需要merge 一下. git branch -a可以查看所有分支\(本地分支+远程分支\)
* git pull 将其所有的分支都更新过来了

### 删除远程分支

* git push origin --delete
* git push origin: 分支名称

### gitignore 创建忽略文件

将不需要提交的文件名放到这个目录中,将来提交的时候就不会将其提交上去

[百度一下你就知道](http://www.baidu.com)

```javascript
    var a = 10;    
    console.log(a);
```

```bash
    git init blog
```

![&#x5C55;&#x793A;&#x56FE;&#x7247;](https://github.com/luggege/book/tree/f7d098fe1f889ccf3b383f621c0b48c599f5fdd3/路径)

