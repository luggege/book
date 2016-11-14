###shell分类
* 1.图形界面shell
* 2.命令行shell(linux下面有bash(默认))
##bash常见命令
命令 [-option] [参数]
1.pwd  print Working Directory : 查看当前目录
2.cd: Change Directory: 改变当前目录
3.ls: 查看当前目录下内容
4.touch: 创建文件
5.cat: 查看文件全部内容
6.more/less: 查看文件(空格: 分页读取;回车: 换行)
7.rm: (remove): 删除文件(rm -r css: 递归来删非空文件夹(recursion: 递归))
8.rmdir: 只能删除空的文件夹
9.mv(move): 剪切操作 (可以改名)
10.cp(copy): 复制
11.head: 查看文件前几行(-n 5/ -5)
12.tail: 查看文件后几行
13.tab: 自动补全
14.history: 查看历史操作

17.管道符: 上一个命名的输出结果当做下一个命令的输入结果传递过去
##vi编辑器
###三种模式
命令模式 (i/a) 输入模式 (:) 末行模式
###末行模式:
*w  q  q!不保存强制提出
*:set nu设置行号
###命令模式
zz保存并退出
dd删除当前行
/u撤销
yy复制当前行

##远程
除自己电脑之外的都叫远程

##Git
>分布式的版本控制系统
###git init 创建.git仓库
>2.git config 配置用户信息(只需要配置一次)
>3.git status
>4.git add
>5.git checkout 将缓存区的内容还原到工作区
>6.git commit -m  永久存盘(必须添编号)
>7.git log 查看当前版本/存盘点/历史
>8.git reset --hard 提交ID









