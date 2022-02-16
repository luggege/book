### npm install && npm ci 区别

* 使用npm ci，当 package.json 和 package-lock.json 依赖不匹配时，会报错并停止安装
* 如果有node\_modules文件，npm ci则会先删除该文件夹，然后安装
* npm ci 无法单独安装某个依赖
* npm ci 更快，因为不会与已经下好的node\_modules进行版本比较
* npm ci 不会更改package.json 和 package-lock.json，安装**冻结**，npm i 则会依据package.json 更新 package-lock.json（\* ^ ~ ：大版本 次版本 小版本）

因此，最好使用npm ci，他会严格按照package-lock.json中指定版本进行安装，并且会对比package.json 和 package-lock.json两个文件中的依赖，防止由错误的依赖造成的版本故障

