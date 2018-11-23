# 客户端存储

## web存储

### localstorage&sessionStorage的区别: 有效期和作用域

#### localstorage:

1. 数据存储**永久性**永不过期: 除非刻意删除或者设置过期时间

2. **作用域**限定在**文档源**: 只有同源的文档才可共享localstorage数据

3. 作用域受**浏览器**供应商限制: 不同浏览器不可共享

#### sessionStorage:

1. 有效期随窗口**标签页的关闭**而消失: sessionStorage存储的数据即被删除
2. 作用域限定在文档源
3. 不同浏览器不可共享sessionStorage数据
4. 同一浏览器不同窗口，无法共享：每次通过复制地址新打开的标签页即使同源都会重新初始化一个session，故无法共享。但是通过a链接或者window.open打开的新标签页之间共享sessionStorage

#### 存储API

1. ```js
   1. setItem():          localstorage.setItem('a', 1);
   2. getItem():          localstorage.getItem('a');
   3. removeItem():       localstorage.removeItem('a');
   4. 非IE8中,使用delete操作
   5. clear():            localstorage.clear();  清空全部
   6. 枚举
   for(var i = 0; i < localStorage.length; i++){
       var name = localStorage.key(i);
       var value = localStorage.getItem(name);
   }
   ```

## cookie

> 用户担心cookie的不安全性，可能会将浏览器的cookie禁用，可以通过navigator.cookieEnabled这个属性检测\(true：cookie启用，flase：禁用\)。
>
> 每个cookie的**有效期**和**作用域**都需要通过**字符串**的形式读写document对象的cookie属性

## IE User Data

> IE8以前,web存储的替代方案

## 离线web应用

## web数据库

## 文件系统API


