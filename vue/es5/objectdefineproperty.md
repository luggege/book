### Object.defineProperty\(obj, prop, descriptor\)定义对象属性

**作用：**

* 为对象设置一个属性，并设置值
* 给该属性设置描述符（数据描述符/访问描述符）

### 数据描述符：value/writable

```js
let obj = {};
Object.defineProperty(obj, "a", {
    value: 111,        // 属性值
    writable: false,   // 是否可重写值, 默认false
    enumerable: false, // 是否可枚举, 默认false
    configurable: false// 是否可修改以上配置, 默认false
});
```

### 两个描述符共有的必选项：enumerable/configurable

```js
//configurable: true
1. 是否可删除
Object.defineProperty(obj, 'q', {
    value: '222',
    configurable: true
})
delete obj.q // true

2. 是否可重修改
Object.defineProperty(obj, 'q', {
    value: '111',
    configurable: false
})
// obj.q ==> '111'

Object.defineProperty(obj, 'a', {
    value: '333'
})
// Uncaught TypeError: Cannot redefine property: a
```

### 访问描述符：get/set

> 其实并没有getter/setter这样的属性，只是两个概念，与之对应的是两个访问描述符

#### 当设置/获取某个属性时，提供getter/setter方法

```js
1. 当设置getter/setter方法时，不允许value和writable出现
Object.defineProperty(obj, 'f', {
    value: '444',
    writable: true,
    enumerable: true,
    configurable: false,
    get: function(){
        return value
    },
    set: function(newValue){
        return value = newValue
    }
})
// Uncaught TypeError: Invalid property descriptor. Cannot both specify accessors and a value or writable attribute, #<Object>
```

```js
var initValue = 'aaa'
Object.defineProperty(obj, 'x', {
    enumerable: false,
    configurable: false,
    get: function(){
        return initValue
    },
    set: function(newValue){
        return initValue = newValue
    }
})
obj.x      // aaa
obj.x = 111
obj.x      // 111
```



