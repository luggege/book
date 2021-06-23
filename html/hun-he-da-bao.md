# 混合打包

## 环境配置

### 1. node环境配置 \(npm包管理工具\)

### 2. ant安装及环境配置\(ant: Apache基金会下的跨平台构建工具,实现项目的自动构建和部署功能\)

> 官方主页**下载**\([http://ant.apache.org](http://ant.apache.org)\)===&gt;Download\(安装文件/源文件/手册 只需要第一个即可,解压之后全局配置\)  
> 系统变量 1. ant\_home \( C:\MySoft\ant\apache-ant-1.10.1-bin \) 2.编辑: path\( C:\MySoft\ant\apache-ant-1.10.1-bin\bin \) 3.编辑: classPath\( C:\MySoft\ant\apache-ant-1.10.1-bin\lib \)
>
> **检验ant是否安装:**命令行工具:ant 或者 ant -version\(ant -v\)

### 3. java环境 \(Android ADT需要该环境,下载并配置jdk\(java开发工具包\)的环境变量:java\_home\)

> java\_home: "C:\Program Files\Java\jdk1.8.0\_91"  
> path: ";%JAVA\_HOME%\bin;%JAVA\_HOME%\jre\bin;"  
> classPath: ".;%JAVA\_HOME%\lib\dt.jar;%JAVA\_HOME%\lib\tools.jar;"
>
> **检验java环境是否安装:**javac 或者 java -version

### 4. C++环境\(node需要\)

### 5. 安装Android sdk\(软件开发工具包\)

必须安装的5个东西: android-sdk / platform-tools / Tools / build-tools / extras

> **配置环境变量:**  
> ANDROID\_HOME: C:\Users\admin\AppData\Local\Android\android-sdk\(有tools文件的根目录\)  
> path: %ANDROID\_HOME%\tools;%ANDROID\_HOME%\platform-tools

**检验android:**adb

![](/assets/ionic.png)

## 项目依赖

### 1.安装cordova: npm install -g cordova

**检验**: cordova -v

### 2.安装ionic环境: npm install -g ionic

**检验**: ionic -v

> **一次性安装 cordova 和 ionic**  
> 使用淘宝镜像: npm install -g cnpm --registry=[https://registry.npm.taobao.org](https://registry.npm.taobao.org); 完成之后执行 cnpm install -g cordova ionic



