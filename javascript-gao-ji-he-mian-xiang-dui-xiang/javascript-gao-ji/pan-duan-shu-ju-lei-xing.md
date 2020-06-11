### 判断数据类型

1. typeof：Array、Date、Error都为Object
2. instanceof：`[] instanceof Array`**构造函数的原型**是不是在给定对象的原型链上
3. Object.prototype.isPrototypeOf\(\[\]\)：Object.prototype是否在\[\]的**原型链**上
4. Object.prototype.toString.call\(\)：根据内部的this返回一个类似于这样的字符串'\[object constructorName\]'\(这个实例的构造函数的名\)
5. Array.isArray\(\)

**封装一个获取变量准确类型的函数**

```js
function gettype(obj) {
  var type = typeof obj;

  if (type !== 'object') {
    return type;
  }
  //如果不是object类型的数据，直接用typeof就能判断出来

  //如果是object类型数据，准确判断类型必须使用Object.prototype.toString.call(obj)的方式才能判断
  return Object.prototype.toString.call(obj).replace(/^\[object (\S+)\]$/, '$1');
}
```

#### 为什么要用Object原型上的toString方法

> Number、Boolean、String、Array、Function...每一个内置类都改写了Object原型上的toString方法，故表现形式不一，所以通过call改变this指向，统一使用Object原型的toString方法来判断类型

```js
[1, 2, 3].toString()    // "1,2,3"

Array.prototype.hasOwnProperty('toString') // true

delete Array.prototype.toString            

Array.prototype.hasOwnProperty('toString') // false

[1, 2, 3].toString()                       // "[object Array]"
```



