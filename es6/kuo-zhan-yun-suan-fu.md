### 扩展运算符

* 将**数组**转为用逗号分隔的参数序列

```javascript
console.log(0, ...[1, 2, 3], 4)            // 0 1 2 3 4

console.log(...[])                         // undefined

// 只有函数调用的时候，扩展符才可以放到圆括号里
console.log((...[3]))                      // Uncaught SyntaxError: Unexpected number
```

应用：

* * 复制数组（如果成员是复合数据类型的数据，就是**浅复制**，可借助concat间接实现深复制）
  * 合并数组
  * 与解构赋值结合
  * ```js
    const list = [1, 2, 3, 4, 5];

    // ES5
    const first = list[0]
    const rest = list.slice(1)

    // ES6
    const [first, ...rest] = list
    first // 1
    rest  // [2, 3, 4, 5]
    ```

    **注意：**扩展运算符用于数组赋值只能放在参数的最后一位，否则报错

  * 字符串：转为真正的数组

  * ```js
    [...'hello']
    // ['h', 'e', 'l', 'l', 'o']
    ```
* 将**对象**的可遍历属性拷贝到当前对象中

```js
let z = {a: 1, b: 2}
let n = { ...z }
n // {a: 1, b: 2}

// 数组是特殊的对象
let foo = { ...['a', 'b', 'c'] }
foo //{0: "a", 1: "b", 2: "c"}
```

```js
// 扩展运算符的解构赋值，只能复制自身属性，不能复制继承自原型对象的属性，且只能放在参数的最后一位
let o1 = Object.create({b: 2})
o1.a = 1
let {...o2} = o1
o2.a   // 1
o2.b   // undefined

o1.c = 333
let {...o3, c} = o1  // Uncaught SyntaxError: Rest element must be last element

let obj = { a: { b: 1 } };
let { ...x } = obj;
obj.a.b = 2;
x.a.b   // 2
```

应用

* * 复制（解构赋值的拷贝是**浅拷贝**）
  * 合并（对象的扩展运算符等同于使用Object.assign\(\)方法，只会返回自身的、可枚举属性。（成员是**基础数据**则**深拷贝**，**复合数据类型**则**浅拷贝**））

#### 替代函数的 apply 方法

```javascript
function fn(x, y, z) {
    console.log(x, y, z)
}

// ES5
var args = [1, 2, 3]
fn.apply(null, args)

// ES6简洁写法
fn(...args)
```

```javascript
// 将一个数组添加到另一个数组的尾部
var arr1 = [1, 2, 3];
var arr2 = [4, 5, 6];

// ES5
Array.prototype.push.apply(arr1, arr2)

// ES6
arr1.push(...arr2)
```



