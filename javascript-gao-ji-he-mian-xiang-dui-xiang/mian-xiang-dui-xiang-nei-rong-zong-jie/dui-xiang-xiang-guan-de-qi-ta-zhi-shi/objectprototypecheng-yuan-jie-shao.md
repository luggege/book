# Object.prototype成员介绍

## `Object.prototype`常用成员

| 成员 | 描述 |
| :--- | :--- |
| `Object.prototype.constructor` | 指向与其相关的构造函数 |
| `Object.prototype.__proto__` | 指向当对象被实例化的时候，用作原型的对象，通过 对象. \_\_proto\_\_  访问原型对象。 |
| `Object.prototype.hasOwnProperty()` | 返回一个布尔值 ，表示某个对象是否含有指定的属性，而且此属性**非原型链继承**的。 |
| `Object.prototype.isPrototypeOf()` | 返回一个布尔值，对象1. isPrototypeOf \(对象2\);    判断对象1是否是对象2的原型链中。 |
| `Object.prototype.propertyIsEnumerable` | obj.propertyIsEnumerable\(prop\)用来表示指定的属性名是否可枚举的布尔值 |
| `Object.prototype.toString()/toLocaleString` | 返回对象的字符串表示。 |
| `Object.prototype.valueOf()` | 返回指定对象的原始值。（在对象参与运算时,默认先去调用对象的ValueOf方法,若无法进行运算,再去调用p的toString方法运算） |



