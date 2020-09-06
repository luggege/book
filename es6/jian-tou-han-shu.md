## 箭头函数

> 匿名函数的简化

```js
x => x * x
// 等价于
function(x){x*x}
```

* 单参数可以省略（）
* 单语句可以省略  {} 和 return

### 为什么要使用箭头函数

* 语法糖、简洁

* 解决this问题

* * 普通函数this指向调用者

```js
var obj = {
    birth: 1990,
    getAge: function(){
        var b = this.birth;
        console.log(this.birth)  // 1990
        var fn = function(){
            console.log(this.birth) // undefined
            return new Date().getFullYear() - this.birth;
        }
        return fn();
    }
} 
obj.getAge()  // NaN

// 一般使用that替换this
var obj = {
    birth: 1990,
    getAge: function(){
        var b = this.birth;
        var that = this;
        console.log(this.birth)  // 1990
        var fn = function(){
            console.log(that.birth)  //1990
            return new Date().getFullYear - that.birth;
        }
        return fn();
    }
}
obj.getAge()  // 30
```

* * 箭头函数this由词法作用域，上下文确定

```js
var obj = {
    birth: 1990,
    getAge: function(year){
        var b = this.birth;
        var fn = () => {
            return new Date().getFullYear() - this.birth;   // this指向obj对象
        }
        return fn();
    }
}
obj.getAge()   // 30
```

* * 正因为箭头函数中的this由词法作用域决定，所以用call\(\)和apply\(\)调用箭头函数时的无法改变this，即第一个参数失效

```js
var obj = {
    birth: 1990,
    getAge: function(year){
        var b = this.birth;
        var fn = (y) => {
            return y - this.birth;
        }
        return fn.call({birth: 2000}, year);
    }
}
obj.getAge(2020)   // 30
```

### 注意

* 箭头函数不能当作构造函数使用，new 的时候报错
* 没有prototype属性
* 返回对象时必须用圆括号包起来

```js
var func = () => {foo: 1}
func()   // undefined

var func = () => ({foo: 1})
func()   // {foo: 1}
// 或者
var func = () => {return {foo: 1}}
func()   // {foo: 1}
```



