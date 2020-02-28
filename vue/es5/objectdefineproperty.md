### Object.defineProperty\(obj, prop, descriptor\)定义对象属性

```js
Object.defineProperty(obj, "newDataProperty", {
  value: 101,       // 属性值
  writable: true,   // 是否可重写值
  enumerable: true, // 是否可枚举
  configurable: true// 是否可修改以上配置
});
```



