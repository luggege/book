### async/await

> Generator函数的语法糖，本质是基于Promise的封装

* async函数返回一个Promise实例
* async和await之间的代码同步执行，相当于new Promise传入的参数
* await之后的代码相当于.then传入的回调（new Promise\(resolve =&gt; {}\).then\(\)）
* async内部return语句返回的值，会作为then方法的参数

```js
async function f() {
    return 'Hello World'
}
f().then(res => console.log(res))  // Hello World
```

```js
// 红黄绿灯间隔1s交替执行
function fn(color, delay) {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            console.log(color);
            resolve()
        }, delay)
    })
}

/*
const loop = () => {
    fn('green', 1000).then(() => {
        fn('yellow', 1000).then(() => {
            fn('red', 1000).then(() => {
                loop();
            });
        })
    })
}
*/
const loop = async () => {
    await fn('green', 1000);
    await fn('yellow', 1000);
    await fn('red', 1000);
    loop();
}
loop()
```



