### 浏览器存储机制

> web存储：localstorage & sessionStorage的区别: 有效期和作用域，同时兼容当前所有主流浏览器

#### localstorage:

1. 数据存储**永久性**永不过期: 除非刻意删除或者设置过期时间
2. **作用域**限定在**文档源**: 只有同源的文档才可共享localstorage数据，大小5M左右
3. 作用域受**浏览器**供应商限制: 不同浏览器不可共享

#### sessionStorage:

1. **有效期**随窗口**标签页的关闭**而消失: sessionStorage存储的数据即被删除
2. **作用域**限定在**文档源：**不同浏览器不可共享sessionStorage数据，大小5M左右
3. 同一浏览器不同窗口，**无法共享**：每次通过复制地址新打开的标签页即使同源都会重新初始化一个session，故无法共享。但是通过**a链接或者window.open**打开的新标签页之间**共享**sessionStorage（低版本的Chrome可以，高版本的及火狐还是会生成新的session，需要给a链接添加rel=“opener”属性即可）

存储API

1. ```javascript
   1. localStorage.setItem('a', 1);
   2. localStorage.getItem('a');
   3. localStorage.removeItem('a');
   4. 非IE8中,使用delete操作
   5. localStorage.clear();  清空全部
   6. 枚举
   for(var i = 0; i < localStorage.length; i++){
       var name = localStorage.key(i);
       var value = localStorage.getItem(name);
   }
   ```

#### **cookie**

> **cookie在浏览器和服务器间来回传递**
>
> 用户担心cookie的不安全性，可能会将浏览器的cookie禁用，可以通过navigator.cookieEnabled这个属性检测\(true：cookie启用，flase：禁用\)。
>
> 每个cookie的**有效期**和**作用域**都需要通过**字符串**的形式读写document对象的cookie属性来指定
>
> 每个domain最多20条cookie，每条cookie长度不能超过4KB，否则会被截掉

1. **有效期**很短暂，随**浏览器关闭而删除**cookie文件。但与sessionStorage不同的是：cookie的有效期是整个**浏览器进程**而不是单个窗口
2. **作用域**是通过**文档源**和**文档路径**来确定的，默认情况下，cookie和创建他的web页面有关，并对该页面及其该页面**同目录**或者**子目录**的其他页面可见（[http://www.baidu.com/catalog/index.html创建的cookie，在http://www.baidu.com/catalog/test.html和http://www.baidu.com/catalog/test/index.html是可见的）](http://www.baidu.com/catalog/index.html创建的cookie,在http://www.baidu.com/catalog/test.html和http://www.baidu.com/catalog/test/index.html是可见的）)

```js
document.cookie
```

##### cookie的跨域问题：

domain表示的是cookie所在的域，默认为请求的地址，如网址为www.study.com/study，那么**domain**默认为**www.study.com**。而跨域访问，如域A为t1.study.com，域B为t2.study.com，那么在域A生产一个令域A和域B都能访问的cookie就要将该cookie的domain设置为**.study.com**；如果要在域A生产一个令域A不能访问而域B能访问的cookie就要将该cookie的domain设置为t2.study.com。

注意：一般在域名前是需要加一个"."的，如"domain=.study.com"

| 参数 | 描述 |
| :--- | :--- |
| name |  |
| value |  |
| domain | 子域 |
| path | 一般设为/，表示该站点下所有页面都可以访问 |
| expire | 过期时间，不设置则随浏览器关闭消失 |
| httpOnly | 若开启，则脚本无法获取cookie |
| secure | 若设置，则只允许https协议连接可以访问cookie |

#### IE User Data

> IE8以前,web存储的替代方案

#### 离线web应用

#### web数据库

#### 文件系统API



