# 算法

> 递归
>
> * 定义: **在函数内部自己调用函数自己** 
> * 死递归:没有**递归结束条件** 
> * 化归思想：化繁为简，化难为易

#### 利用setTimeout实现setInterval

```js
function interval(){
    var timer = setTimeout(() => {
        console.log(1111)
        interval()
        clearTimeout(timer)
    }, 1000)
}

interval()
```

#### 斐波那契数列

> Fibonacci 数列: 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, … 求其第 n 项.

递推关系:`fn(n) == fn(n-1) + fn(n - 2)`

```javascript
function fib( n ) {
    if ( n == 0 || n == 1 ) 
    return 1;        
    return fib( n - 1 ) + fib( n - 2 );
}
```

## 例子:

> 1, 2, 3, 4, 5, ..., 100 求和

1. 首先假定递归函数已经写好, 假设是`foo`. 即`foo(100)`就是求`1`到`100`的和
2. 寻找递推关系. 就是`n`与`n-1`, 或`n-2`之间的关系:`foo( n ) == n + foo( n - 1 )`

```javascript
var res = foo(100);

var res = foo(99) + 100;
```

**将递推结构转换为递归体**

```javascript
function foo(n){
   return foo(n-1) + n;
};
```

上面就是利用了化归思想：

* 将 求 100 转换为 求 99
* 将 求 99 转换为 求 98
* ...
* 将求 2 转换为 求 1
* 求 1 结果就是 1
* 即: foo\( 1 \) 是 1

**将临界条件加到递归体中\(求1的结果为1\)**

```javascript
function foo(n){
    if(n === 1){
        return 1;
    }
    return foo(n-1) + n;
};
foo(100);
```

> 求 1, 3, 5, 7, 9, ... 第`n`项的结果与前`n`项和. 序号从`0`开始

**先看求第**`n`**项**

* 首先假定递归函数已经写好, 假设是`fn`. 那么第`n`项就是`fn(n)`

* 找递推关系:`fn(n) == f(n-1) + 2`

* 递归体

```javascript
function fn(n) {
    return fn(n-1) + 2;
}
```

1. 找临界条件
   * 求 n -&gt; n-1
   * 求 n-1 -&gt; n-2
   * ...
   * 求 1 -&gt; 0
   * 求 第 0 项, 就是 1
2. 加入临界条件

```javascript
function fn(n) {
  if( n == 0 ) {
    return 1;
  }
  return fn( n-1 ) + 2;
}
```

**再看求前**`n`**项和**

* 假设已完成, sum\( n \) 就是前 n 项和

* 找递推关系: 前 n 项和 等于 第 n 项 + 前 n-1 项的和

* 递归体

```javascript
function sum( n ) {
  return fn( n ) + sum( n - 1 );
}
```

1. 找临界条件
   * `n == 1`结果为 1
2. 加入临界条件

```javascript
function sum( n ) {
  if (n == 0) {
    return 1;
  }
  return fn(n) + sum(n - 1);
}
```

> 2, 4, 6, 8, 10 第 n 项与 前 n 项和

解题方法和上一题一样。

> 现有数列: 1, 1, 2, 4, 7, 11, 16, … 求 第 n 项, 求前 n 项和.

**求第**`n`**项**

1. 假设已经得到结果 fn, fn\( 10 \) 就是第 10 项
2. 找递推关系
   * 0, 1 =&gt; fn\( 0 \) + 0 = fn\( 1 \)
   * 1, 2 =&gt; fn\( 1 \) + 1 = fn\( 2 \)
   * 2, 3 =&gt; fn\( 2 \) + 2 = fn\( 3 \)
   * ...
   * n-1, n =&gt; fn\( n-1 \) + n - 1 = fn\( n \)
3. 递归体也就清楚了
4. 临界条件是 n == 0 =&gt; 1

```javascript
function fn( n ) {
    if( n == 0 ) 
    return 1;
    return fn( n-1 ) + n - 1;
}
```

**前**`n`**项和**

```javascript
function sum( n ) {
    if ( n == 0 ) 
    return 1;
    return sum( n - 1 ) + fn( n );
}
```

> 阶乘：一个数字的阶乘表示的是从 1 开始 累乘到这个数字. 例如 3! 表示 1\_2\_3. 5! 就是 1\_2\_3\_4\_5. 规定 0 没有阶乘, 阶乘从1开始。

求n的阶乘

```javascript
function foo ( n ) {
    if ( n == 1 ) 
    return 1;
    return foo( n - 1 ) * n;
}
```

> 求幂

* 求幂就是求 某一个数 几次方
* 2\*2 2 的 平方, 2 的 2 次方
* 求 n 的 m 次方
* 最终要得到一个函数 power\( n, m \)
* n 的 m 次方就是 m 个 n 相乘 即 n 乘以 \(m-1\) 个 n 相乘

```javascript
function power ( n, m ) {
    if ( m == 1 ) 
    return n;
    return power( n, m - 1 ) * n;
}
```



