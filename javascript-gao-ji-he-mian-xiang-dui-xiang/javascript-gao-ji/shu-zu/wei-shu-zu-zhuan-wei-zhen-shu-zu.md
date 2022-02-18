### 伪数组转数组方式

> 类数组/伪数组：按照**索引**存储数据，且有**length**属性的**对象**

```js
let obj = {length: 0}
obj[obj.length++] = 1
obj[obj.length++] = 2

// 1. push
var a = []
Array.prototype.push.apply(a, obj)

// 2. concat
var b = []
var bNew = Array.prototype.concat.apply(b, obj)

// 3. slice
Array.prototype.slice.apply(obj)

// 4. 普通遍历赋值

// 5. Array.from(obj)
```

分析：

```javascript
// 传统的做法：
var a = {};
a[ 0 ] = 'a';
a[ 1 ] = 'b';
a.length = 2;

// 使用数组自带的方法 concat
// 如果参数中有数组会把参数数组展开
// 语法: arr.concat( 1, 2, 3, [ 4, [ 5 ] ] );
// 特点：不修改原数组
var arr = [];
var newArr = arr.concat( a );

// 由于a是伪数组, 只是长得像数组. 所以上面的代码不能成功，不能使用concat方法。
```

但是`apply`方法有一个特性, 可以将数组或伪数组作为参数。（IE8不支持伪数组操作）

```javascript
foo.apply( obj, 伪数组 ); 
// IE8 不支持
```

利用`apply`方法，可以写出以下

```javascript
//将伪数组 a 作为 apply 的第二个参数
var newArr = Array.prototype.concat.apply( [], a )
```

处理数组转换, 实际上就是将元素一个一个的取出来构成一个新数组, 凡是涉及到该操作的方法理论上都可以。

**push方法**

```javascript
//将这三个元素依次加到数组中, 返回arr的个数
arr.push( 1, 2, 3 ); 

// 伪数组
var a = { length: 0 }; 

a[ a.length++ ] = 'abc'; 
// a[ 0 ] = 'abc'; a.length++;
a[ a.length++ ] = 'def';

// 使用一个空数组, 将元素一个个放到数组中即可
var arr = [];

// 此时不会将元素展开, 而是将这个伪数组作为一个元素加到数组中
// arr.push( a );

// 再次利用 apply 可以展开伪数组的特征
// 利用 apply 可以展开伪数组的特性, 这里就相当于 arr.push( a[0], a[1] )
arr.push.apply( arr, a );  // 或者 Array.prototype.push.apply(arr, a)
```





