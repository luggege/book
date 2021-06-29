### call、apply、bind的作用与区别

> call、apply、bind是Function.prototype的方法，所以每个function 实例都有这三个方法

* 相同点

* * 改变this指向
* 不同点

* * call的后边参数需要**逐个**列出来
  * apply的后边参数是一个**数组**
  * bind**返回的是一个函数（需再次调用）**，参数需要**逐个**列出来

```js
function add(c, d){
    return this.a + this.b + c + d
}
var obj = {a: 1, b: 2};

add.call(obj, 3, 4)       // 1 + 2 + 3 + 4
add.apply(obj, [3, 4])    // 1 + 2 + 3 + 4
```

```js
var name = 'Rose', age = 20;
var obj = {
    name: 'Jack',
    // this指向window
    objAge: this.age,
    show: function(from, to) {
        // this指向obj
        console.log(this.name + '年龄：' + this.age + '，来自：' + from + '，现居：' + to)
    }
}

obj.show('山西','北京')    // Jack年龄：undefined，来自：山西，现居：北京
obj.objAge               // 20


var newObj = {
    name: 'lucy',
    age: 99
}

obj.show.call(newObj, '山西', '北京')      // lucy年龄：99，来自：山西，现居：北京
obj.show.apply(newObj, ['山西', '北京'])   // lucy年龄：99，来自：山西，现居：北京
obj.show.bind(newObj, '山西', '北京')()    // lucy年龄：99，来自：山西，现居：北京
```



