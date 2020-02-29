# Object.assign\(\)

### assign：Object.assign\(target, source1,  source2\)方法用于将源对象自身的所有可枚举属性复制到目标对象

1. ```javascript
   // 1. 源对象属性复制到目标对象
   var target = {a: 1};
   var source = {b: 2};
   Object.assign(target, source)  // {a: 1, b: 2}

   // 2. 如有同名属性, 后面覆盖前面
   var target = {a: 1, b: 2};
   var source1 = {b: 2, c: 3};
   var source2 = {c: 4, d: 5};
   Object.assign(target, source1, source2) // {a: 1, b: 2, c: 4, d: 5}

   // 3. 只有一个参数, 直接返回改参数
   var target = {a: 1};
   Object.assign(target) // {a: 1}

   // 4.1 undefined/null 作为目标对象, 由于无法转成对象, 会报错
   Object.assign(undefined)
   Object.assign(null) // VM38563:1 Uncaught TypeError: Cannot convert undefined or null to object

   // 4.2 undefined/null 作为源对象, 无法转成对象, 便会跳过
   var target = {a: 1};
   Object.assign(target, undefined) // {a: 1}
   Object.assign(target, null) // {a: 1}

   // 5. 其他类型(字符串, 布尔, 数值), 不在首参数也不会报错, 但是字符串会以数组形式复制到目标对象, 其他不会
   var str = 'abc';
   var bool = true
   var num = 10;
   Object.assign(str) // String {"abc"}
   Object.assign(bool) // Boolean {true}
   Object.assign(num) // Number {10}
   Object.assign({}, str, bool, num); // {0: "a", 1: "b", 2: "c"}

   // 6.1 如果源对象的属性的值是对象, 那么目标对象得到的是这个对象的引用
   var obj1 = {a: {b: 1}}
   var obj2 = Object.assign({}, obj1);
   obj1.a.b  // 1
   obj2.a.b // 1

   // 6.2 如果源对象的属性的值是对象, 同名属性时替换而不是添加
   var obj1 = {a: {b: 1, c: 2}}
   var obj2 = {a: {b: 'hello'}}
   Object.assign(obj1, obj2); // a: {b: "hello"}
   ```

### assign用途:

1. 添加属性
2. 添加方法
3. 克隆对象
4. 合并对象



