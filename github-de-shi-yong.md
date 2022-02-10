# github创建自己的电子书

### gitbook editor是本地编辑器

> 关联GitHub方法: Book==&gt;Repository Settings==&gt;填入GitHub地址[https://github.com/luggege/book.git](https://github.com/luggege/book.git%29\)
>
> 本地代码同步到GitHub上==&gt;save==&gt;Publish&Sync

### gitbook.com是线上编辑器\(用GitHub账号登录,关联GitHub\)

### github可以托管利用gitbook editor或者是gitbook.com编写的电子书

> github上的master分支用来保存文档笔记源码\(.md\)
>
> gh-pages分支\(只能叫这个名字\)用来保存利用gitbook build生成\(\_book文件夹中\)的静态文件\(html文件、gitbook样式文件\)

### 最终利用GitHub线上预览自己的电子书 [https://luggege.github.io/book](https://luggege.github.io/book%29\)

### 利用gitbook.com线上编辑的电子书,在线预览[https://luggege.gitbooks.io/book](https://luggege.gitbooks.io/book%29\)

## 如何发布到GitHub

> 我们可以在 GitHub 上创建一个仓库，来管理书籍源码。
>
> **注意**:  
> 源代码保存到 master 分支，\(gitbook build\)编译出来的**静态文件**`_book`**上传到 gh-pages 分支**，这样我们就可以通过 GitHub pages 来发布电子书了。

**具体操作步骤:**

```js
1. 登录GitHub创建一个新仓库,命名为book
2. 克隆远程仓库到本地 git clone https://github.com/luggege/book.git
3. 将分支 push 到仓库：git push -u origin gh-pages
4. 切换到主分支:git checkout master        
> 经过这一步处理，我们已经创建好 gh-pages 分支了，有了这个分支，GitHub 会自动为你分配一个访问网址：http://USERNAME.github.io/book
5. 本地编辑器存放.md文件的位置执行：gitbook build (生成_book文件夹，包含静态文件和样式文件)
6. cd .. 退出一层克隆远程仓库的gh-pages分支并保存为book_build文件夹: git clone -b gh-pages https://github.com/luggege/book.git book_build
7. 复制_book中的静态文件到book_build中
8. 将静态文件push到远程仓库book的gh-pages分支上
9. git add .  
10.git commit -m "add file"
11.git push
```

之后，每次修改之后，都可以将生成的静态文件 copy 到 book\_build 目录，再 push 到远程仓库 book 的 gh-pages 分支。

```js
1.git pull origin master(相当于git fetch + git merge) 拉取指定分支,没必要clone
2.gitbook build (生成静态页面之后放到book_build中)
3.如果报错说明gitbook未安装
4.安装gitbook: npm install -g gitbook-cli
5.检查是否安装成功: gitbook -V
6.如果gitbook build之后生成的页面不能跳转,可使用低版本的gitbook( gitbook build --gitbook=2.3.2 )
7.git add .
8.git commit -m "add file"
9.git push
```

### 如何查看GitHub上有没有本台电脑的ssh keys

* C:\Documents\User\Administrator/.ssh 目 录下。有没有id\_rsa和id\_rsa.pub两个文件,有的话已经生成过,复制id\_rsa.pub中的内容到GitHub即可
* 没有的话重新生成: git命令行输入 `ssh-keygen -t rsa -C "email@email.com"` 即可生成.

### git命令: 全局设置用户名和邮箱

```js
1.查看git配置信息: git config --list
2.查看git用户名: git config user.name
3.查看邮箱配置: git config user.email
4.全局配置用户名: git config --global user.name "lugege"
5.全局配置邮箱: git config --global user.email "luwenxiu@legalminer.com"
```

本地电脑多个账号，多个用户身份提交代码，需要配置多个SSH Key

