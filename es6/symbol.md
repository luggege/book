# Symbol

### 概述

> Symbol是ES6中提出的**第七种JavaScript数据类型**，目的是为了解决对象中**同名属性冲突**的问题。
>
> Symbol值通过Symbol函数生成

```js
1. typeof 类型是 symbol
let symbol1 = Symbol()
symbol1          // Symbol()

let symbol2 = Symbol()
symbol2          // Symbol()

typeof symbol1   // "symbol"

2. 无参的情况不等
symbol1 === symbol2   // false

3. 参数只表示对当前Symbol的描述，也不等
let sym1 = Symbol('foo')
sym1             // Symbol(foo)

let sym2 = Symbol('foo')
sym2             // Symbol(foo)

sym1 === sym2    // false

4. 参数为对象时调用对象内部的toString方法
var obj = {
    toString(){
        return 'abc'
    }
}
let sym4 = Symbol(obj)
sym4             // Symbol(abc)

5. 与其他类型的值参与运算会报错
'I am string' + sym4
// VM62296:1 Uncaught TypeError: Cannot convert a Symbol value to a string

6. Symbol值可显示转为字符串
String(sym4)      // "Symbol(abc)"
sym4.toString()   // "Symbol(abc)"

7. Symbol值可显示转为布尔值
Boolean(sym4)     // true

8. Symbol值转为Number类型报错
Number(sym4)
// VM62568:1 Uncaught TypeError: Cannot convert a Symbol value to a number
```

### 获取Symbol的描述

```js
sym4.description         // "abc"
```

### Symbol作为属性名

```js
var obj = {}

// 可用以下三种方式添加属性
1. obj = {
    [sym2]: "World"
}

2. obj[sym4] = "Hello"

3. Object.defineProperty(obj, sym1, {value: 'haha'})

// {Symbol(foo): "World", Symbol(abc): "Hello", Symbol(foo): "haha"}

// 获取属性方式(不能用点属性方法获取)
1. obj[sym4]      // "Hello"

2. obj['sym4']    // undefined

3. obj.sym4       // undefined

// 相比普通属性
obj.a = 111
// {a: 111, Symbol(foo): "World", Symbol(abc): "Hello", Symbol(foo): "haha"}

1. obj.a      // 111
2. obj["a"]   // 111
3. obj[a]     // VM64118:1 Uncaught ReferenceError: a is not defined
```

### 属性名的遍历

```js
1. 所有Symbol键名的数组
Object.getOwnPropertySymbols(obj)
(3) [Symbol(foo), Symbol(abc), Symbol(foo)]

2. 返回所有常规及Symbol键名的数组
Reflect.ownKeys(obj)
(4) ["a", Symbol(foo), Symbol(abc), Symbol(foo)]
```



