#### 数组的解构赋值

> 解构：从数组和对象中提取值，对变量进行赋值，称为解构。

```js
let [a, b, c] = [1, 2, 3];                             // 1 2 3

let [foo, [[foo1], foo2]] = [1, [[2], 3]]              // 1 2 3

let [ , , third] = ['foo', 'foo1', 'foo2'];            // third => "foo2"

let [x, , z] = [1, 2, 3];                              // x, z => 1, 3

let [head, ...tail] = [1, 2, 3, 4];                   // head, tail => 1, [2, 3, 4]
let [header, footer] = [1, 2, 3, 4];                  // header, footer => 1, 2

let [x, y, ...z] = ['aaa'];                           // aaa undefined []

// 解构不成功，变量值为 undefined
let [f] = []                                          // undefined
let [d, e] = [1]                                      // 1 undefined

// 不完全解构，等号左边的变量只匹配等号右边一部分的数组
let [x, y] = [1, 2, 3];                              // x, y => 1, 2
let [a, [b], d] = [1, [2, 3], 4];                    // a, b, d => 1, 2, 4

// 如果等号右边不是数组，将会报错
let [foo] = 1;
let [foo] = false;                                  // VM1232:1 Uncaught TypeError: false is not iterable
let [foo] = NaN;
let [foo] = undefined;
let [foo] = null;
let [foo] = {};

// 但等号右边是字符串类型不会报错
let [h] = '1'                                       // h => "1"

// Set结构，也可以使用数组的解构赋值
let [o, p, q] = new Set(['a', 'b', 'c'])            // a b c


// *默认值*
let [r = true] = []                                // true
let [s, t = 'bbb'] = ['aaa']                       // aaa bbb
let [u, v = 'bbb'] = ['aaa', undefined]            // aaa bbb
let [w, x = 'bbb'] = ['aaa', 'ccc']                // aaa ccc 
let [uu, vv = 'bbb'] = ['aaa', null]               // aaa null （数组成员严格等于undefined，默认值才会生效。null不严格等于undefined，所以默认值不会生效。）
// *默认值是表达式*
function fn(){
    console.log('aaa')
}
let [abc = fn()] = [1]                             // 1 （因为表达式惰性求值，用到时才执行, 能取到值直接用。）

// 默认值可以引用解构赋值的其他变量，但该变量必须已声明
let [x = 1, y = x] = [];     // x=1; y=1
let [x = 1, y = x] = [2];    // x=2; y=2
let [x = 1, y = x] = [1, 2]; // x=1; y=2
let [x = y, y = 1] = [];     // ReferenceError: y is not defined
```

#### 对象的解构赋值

> 数组的解构：变量是按元素的排列次序相应取值；
>
> 对象的解构：与次序无关，变量必须与属性同名才能取到正确的值。

```js
let { foo, bar } = { foo: 'aaa', bar: 'bbb' }             // foo => "aaa"      bar => "bbb"

// { baz } 相当于 { baz: baz } 的简写，右边对象没有baz属性，所以左边baz变量取不到值
let { baz } = { foo: 'aaa', bar: 'bbb' };                 // baz => undefined

let { a: bbbb } = { a: 'aaaa' }                          // a => a is not defined    bbb => 'aaaa'

let obj = {
    p: [
        'hello',
            { y: 'world' }
    ]
}
let { p, p: [x, y] } = obj                               // p => ["hello", {…}]    x => "hello"  y => { y: 'world' }

// 嵌套赋值
let obj = {};
let arr = [];

({ foo: obj.prop, bar: arr[0] } = { foo: 123, bar: true });// obj => {prop:123}    arr => [true]


// 默认值
let { xx = 3 } = {}                                     // xx => 3
let { xx: yy = 3 } = { xx: 55 }                         // yy => 55
let { aa, bb = 3 } = { aa: 11 }                         // aa => 11  bb => 3
// 默认值生效的条件是属性值严格等于undefined 
let { xxx = 333 } = { xxx: undefined }                  // xxx => 333
let { yyy = 333 } = { yyy: null }                       // yyy => null


// 注意点
1. 避免在行首直接使用大括号，JavaScript将其解释为代码块，使用圆括号解决如下：
let x;
({x} = {x: 1});

2. 左边不放置任何变量也是可以的
({} = [true, false]);
({} = 'abc');
({} = []);

3. 对数组进行对象属性的解构
let {0: first, [array.length - 1]: last} = array       // first => 1  last => 3
```

#### 字符串的解构赋值

```js
// 字符串被转换为一个类似数组的对象
const [a, b, c, d, e] = 'hello'                       // a => 'h', b => 'e', c => 'l', d => 'l', e => 'o'

// 类似数组的对象都有一个length属性，length属性也可以解构赋值
let {length: len} = 'hello'                          // len => 5
```

#### 数值和布尔值的解构赋值

> 解构赋值时，如果等号右边的值不是数组或对象，都会先转为对象

```js
let {toString: s} = 123;
s === Number.prototype.toString                      // true

let {toString: s} = true;
s === Boolean.prototype.toString                     // true

// 由于undefined和null无法转为对象所以会报错
let { prop: ha } = undefined
let { prop: hh } = null     
// VM1317:1 Uncaught TypeError: Cannot destructure property `prop` of 'undefined' or 'null'.
```

#### 函数参数的解构赋值

```js
// 解构成x, y变量来看
function add([x, y]) {
    return x + y
}
add([2, 3])                                          // 5


// 默认值（是为x, y变量指定默认值）
function move({ x = 0, y = 0 } = {}) {
    return [x, y]
}
move({ x: 3, y: 5 })                                // [3, 5]
move({ x: 3 })                                      // [3, 0]
move({})                                            // [0, 0]
move()                                              // [0, 0]

//注意（是为函数参数指定默认值）
function move({ x, y } = { x: 0, y: 0 }) {
    return [x, y]
}
move({ x: 3, y: 5 })                                // [3, 5]
move({ x: 3 })                                      // [3, undefined]
move({})                                            // [undefined, undefined]
move()                                              // [0, 0]
```

#### 不能使用圆括号的情况

```js
// 全部报错 Uncaught SyntaxError: Unexpected token (

1. 变量声明语句
let [(a)] = [1];

let {x: (c)} = {};
let {(x): c} = {};
let ({x: c}) = {};
let {(x: c)} = {};

let { o: ({ p: p }) } = { o: { p: 2 } };

2. 函数参数(也属于变量声明)
function f([(z)]) {
    return z;
}

3. 赋值语句的模式
([a]) = [5]
({ p }) = {p: 1}
```

#### 可以使用圆括号的情况

> 只有一种情况：赋值语句的**非模式**部分

```js
// 正确
[(a)] = [5]
{ p: (p) } = {p: 1}
```

#### 用途

```js
1. 变量交换
let x = 1;
let y = 2;

[x, y] = [y, x]                                    //  [2, 1]

2. 解决函数只能返回一个值的问题
function fn() {
    return [1, 2, 3]
}
let [a, b, c] = fn()                              // a b c => 1 2 3

function f() {
    return {
        foo: 1,
        bar: 2
    }
}
let { foo, bar } = f()                           // foo bar => 1 2

3. 函数参数的定义
function foo([x, y, z]) {
    return [x, y, z]
}
foo([1, 2, 3])                                   // [1, 2, 3]

function example({x, y, z}) {
    return {x, y, z}
}
example({z: 1, y: 2, x: 3})                      // {x: 3, y: 2, z: 1}

4, 提取json数据
let jsonData = {
    name: 'zhangsan',
    value: 'OK',
    data: [1, 2]
}
let {name, value, data: num} = jsonData         // name value num => 'zhangsan' "OK" [1, 2]
```



