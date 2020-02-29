### Object.defineProperty\(obj, prop, descriptor\)定义对象属性

```js
let obj = {};
Object.defineProperty(obj, "a", {
  value: 111,       // 属性值
  writable: false,   // 是否可重写值, 默认false
  enumerable: false, // 是否可枚举, 默认false
  configurable: false// 是否可修改以上配置, 默认false
});
Object.defineProperty(obj, "b", {
  value: 222,       // 属性值
  writable: true,   // 是否可重写值, 默认false
  enumerable: true, // 是否可枚举, 默认false
  configurable: true// 是否可修改以上配置, 默认false
});
```



