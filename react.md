### React

> 用于构建用户界面的Javascript库
>
> ```js
> 1、引入react库
> 2、引入react-dom库，用于支持react操作dom
> 3、引入babel将jsx转为js
> ```

#### 纯函数

> 需满足两个条件：
>
> * 返回值只受参数影响
> * 执行过程中无副作用（有副作用：对外部数据产生了可观察的变化）

```js
// 纯函数
function fn(a, b) {
    return (a + b)
}

// 不纯
function fn() {
    return Math.random()
}
```

```js
// 纯函数
function fn(obj, b) {
    return (obj.x + b)
}
const obj = {x: 2}

// 不纯
function fn(obj, b) {
    obj.x = 3
    return (obj.x + b)
}
const obj = {x: 2}
```

所有React组件都必须是纯函数，并禁止修改其自身props，也不允许修改，遵循单向数据流原则，因为假如可以修改，则会造成跟父组件相关的所有组件的内容修改，就会乱套不可控

#### 受控组件&非受控组件

> 非受控组件：状态现用现取（ref）
>
> ```js
> <input ref={element => this.input1 = element} type="text" />
> ```
>
> 受控组件：状态由React维护（setState存，state取）
>
> ```js
> <input type="text" name="username" onChange={event => this.saveFormData('username', event)}/>
> ```

#### 有状态组件 & 无状态组件

* 有状态组件：属于一个class类，有this，有state，props，可继承，有生命周期
* 无状态组件：属于函数式组件，无state、props，只关注DOM渲染，不关注其他逻辑



